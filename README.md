# React + TypeScript + Vite

## Authentication API

The optional Express API provides MongoDB-backed registration and JWT cookie
sessions. Copy `server/.env.example` to `server/.env`, set a rotated MongoDB
connection string and a long random `JWT_SECRET`, then run:

```bash
npm run server
```

## KisanBazaar Website Overview

KisanBazaar is a responsive farm-to-market marketplace that connects farmers,
bulk buyers, and platform administrators through transparent pricing, commerce
workflows, logistics tracking, and role-based dashboards.

### Public marketplace

- Landing page explaining the marketplace problem, solution, workflow, and impact.
- Product marketplace with search, category filters, sorting, product cards, and
  public browsing.
- Protected product details with farmer information, price transparency, reviews,
  and add-to-cart actions.
- Cart, coupons, product comparison, recently viewed products, checkout, orders,
  shipment tracking, favorites, and reviews.

### Authentication and access

- Registration and login for farmers, bulk buyers, and admins.
- MongoDB-backed users with JWT sessions stored in HTTP-only cookies.
- Role-protected routes and dashboards.
- Guests can browse public marketplace pages but must authenticate for protected
  commerce and portal features.
- Development demo accounts can be seeded with `SEED_DEMO_USERS=true`.

### Farmer portal

Farmers can manage products, inventory, stock alerts, incoming orders, earnings,
payouts, and AI demand insights. The dashboard includes revenue metrics, sales
activity, charts, and harvest planning recommendations.

### Buyer portal

Buyers can review spending, active deliveries, orders, favorites, recommendations,
supplier information, and quotation workflows. A buying assistant provides
frontend demo guidance for sourcing and delivery decisions.

### Admin portal

The admin workspace uses a dark green fixed sidebar and off-white responsive
content area. It includes:

- User directory with search, role/status filters, export controls, and detail
  activity drawers.
- Product catalog with inventory metrics, status indicators, and table/grid views.
- Order processing with KPI cards, status filters, and order detail timelines.
- Logistics with fleet, route, capacity, and shipment monitoring data.
- Analytics with revenue, MAU, conversion, AOV, date-range controls, and trend
  data.

Admin tables use responsive overflow handling so fleet and operational records
remain readable on small screens.

### Logistics and AI

- Route and shipment timeline views.
- Vehicle fleet status, route capacity, delivery progress, and ETA information.
- Demo AI features for crop advice, demand forecasting, price intelligence, buyer
  recommendations, and operational risk signals.
- Floating AI marketplace assistant with visible chat input and quick prompts.

### Profile and account

Authenticated users have a responsive profile page with profile photo upload,
personal and business details, GST information, completion progress, language and
currency preferences, notification settings, password controls, account status,
security options, data download, logout-all-devices, and account deletion
confirmation.

### Responsive experience

- Desktop fixed portal sidebar with reserved content space.
- Mobile full-width layouts with the sidebar hidden to avoid overlap.
- Mobile bottom navigation for Home, Products, Favorites, and Profile.
- Mobile burger menu for dashboard navigation.
- Responsive cards, forms, tables, drawers, charts, and horizontal fleet-table
  scrolling.

### Technology

- React 19, TypeScript, Vite, React Router, TanStack Query, Recharts, and
  Lucide icons.
- Express 5, MongoDB/Mongoose, JWT, bcryptjs, CORS, cookies, and dotenv.
- Frontend and API can run together with `npm run dev:full`.

### Important security notes

Create `server/.env` locally from `server/.env.example`. Keep MongoDB credentials
and JWT secrets out of frontend code, logs, commits, and shared documentation.
Rotate any database credentials that may have been exposed.

Run the frontend and API together with `npm run dev:full`. Never place database
credentials in frontend code or commit `.env` files. Set `SEED_DEMO_USERS=true`
only for development to create the three existing demo accounts.

The browser client sends credentials to `/api/auth/*`; Vite proxies those
requests to `http://localhost:4000` during development. For a separately
deployed API, set `VITE_API_URL` to the API base URL (for example,
`https://api.example.com/api`) and configure `CLIENT_ORIGIN` on the server.

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])

```

You can also install [eslint-plugin-react-x](https://npmx.dev/package/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://npmx.dev/package/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])

```

```
Project-01
├─ .claude
│  └─ agents
│     └─ my agent.agent.md
├─ eslint.config.js
├─ index.html
├─ package-lock.json
├─ package.json
├─ public
│  ├─ favicon.svg
│  └─ icons.svg
├─ README.md
├─ src
│  ├─ App.css
│  ├─ App.tsx
│  ├─ ARCHITECTURE.md
│  ├─ assets
│  │  ├─ hero.png
│  │  ├─ react.svg
│  │  └─ vite.svg
│  ├─ components
│  ├─ features
│  │  ├─ admin
│  │  ├─ ai
│  │  ├─ analytics
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ auth
│  │  ├─ buyer
│  │  ├─ buyer-favorites
│  │  │  ├─ buyer-favorites.css
│  │  │  ├─ BuyerFavorites.tsx
│  │  │  ├─ FavoriteButton.tsx
│  │  │  ├─ index.ts
│  │  │  └─ service.ts
│  │  ├─ checkout
│  │  ├─ commerce-tools
│  │  │  ├─ commerce-tools.css
│  │  │  ├─ CommerceTools.tsx
│  │  │  ├─ index.ts
│  │  │  └─ service.ts
│  │  ├─ demand-forecasting
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ farmer
│  │  ├─ farmer-dashboard
│  │  │  ├─ components
│  │  │  │  └─ FarmerDashboard.tsx
│  │  │  └─ index.ts
│  │  ├─ farmer-inventory
│  │  │  ├─ constants.ts
│  │  │  ├─ farmer-inventory.css
│  │  │  ├─ FarmerInventory.tsx
│  │  │  ├─ hooks.ts
│  │  │  ├─ index.ts
│  │  │  ├─ services.ts
│  │  │  └─ types.ts
│  │  ├─ impact
│  │  ├─ logistics
│  │  ├─ market-insights
│  │  │  ├─ index.ts
│  │  │  ├─ market-insights.css
│  │  │  ├─ MarketInsights.tsx
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ marketplace
│  │  ├─ notifications
│  │  │  ├─ index.ts
│  │  │  ├─ NotificationCenter.tsx
│  │  │  ├─ notifications.css
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ order-tracking
│  │  │  ├─ constants.ts
│  │  │  ├─ hooks.ts
│  │  │  ├─ index.ts
│  │  │  ├─ order-tracking.css
│  │  │  ├─ OrderTrackingPanel.tsx
│  │  │  ├─ services.ts
│  │  │  └─ types.ts
│  │  ├─ orders
│  │  ├─ portal
│  │  │  └─ DashboardPortal.tsx
│  │  ├─ price-intelligence
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ route-optimization
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  ├─ types
│  │  │  └─ utils
│  │  ├─ supply-chain
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  └─ workflow-suite
│  │     ├─ index.ts
│  │     ├─ workflow-suite.css
│  │     └─ WorkflowWorkspace.tsx
│  ├─ hooks
│  ├─ index.css
│  ├─ layouts
│  │  └─ README.md
│  ├─ lib
│  ├─ main.tsx
│  ├─ mock
│  │  ├─ buyers.ts
│  │  ├─ data
│  │  ├─ farmers.ts
│  │  ├─ forecasts.ts
│  │  ├─ notifications.ts
│  │  ├─ orders.ts
│  │  ├─ products.ts
│  │  ├─ shipments.ts
│  │  └─ users.ts
│  ├─ pages
│  │  └─ README.md
│  ├─ services
│  │  ├─ aiService.ts
│  │  ├─ analyticsService.ts
│  │  ├─ authService.ts
│  │  ├─ buyerService.ts
│  │  ├─ farmerService.ts
│  │  ├─ logisticsService.ts
│  │  ├─ notificationService.ts
│  │  ├─ orderService.ts
│  │  ├─ paymentService.ts
│  │  └─ productService.ts
│  ├─ store
│  │  ├─ authStore.ts
│  │  ├─ cartStore.ts
│  │  └─ slices
│  ├─ types
│  │  └─ api.ts
│  └─ utils
│     └─ storage.ts
├─ tsconfig.app.json
├─ tsconfig.json
├─ tsconfig.node.json
└─ vite.config.ts

```
```
Project-01
├─ .claude
│  └─ agents
│     └─ my agent.agent.md
├─ eslint.config.js
├─ index.html
├─ package-lock.json
├─ package.json
├─ public
│  ├─ favicon.svg
│  └─ icons.svg
├─ README.md
├─ server
│  ├─ auth.js
│  ├─ config
│  │  └─ db.js
│  ├─ index.js
│  └─ models
│     └─ User.js
├─ src
│  ├─ App.css
│  ├─ App.tsx
│  ├─ ARCHITECTURE.md
│  ├─ assets
│  │  ├─ hero.png
│  │  ├─ react.svg
│  │  └─ vite.svg
│  ├─ components
│  ├─ features
│  │  ├─ admin
│  │  ├─ ai
│  │  ├─ ai-crop-advisor
│  │  │  ├─ ai-crop-advisor.css
│  │  │  ├─ CropAdvisor.tsx
│  │  │  ├─ index.ts
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ analytics
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ auth
│  │  ├─ buyer
│  │  ├─ buyer-favorites
│  │  │  ├─ buyer-favorites.css
│  │  │  ├─ BuyerFavorites.tsx
│  │  │  ├─ FavoriteButton.tsx
│  │  │  ├─ index.ts
│  │  │  └─ service.ts
│  │  ├─ checkout
│  │  ├─ commerce-tools
│  │  │  ├─ commerce-tools.css
│  │  │  ├─ CommerceTools.tsx
│  │  │  ├─ index.ts
│  │  │  └─ service.ts
│  │  ├─ demand-forecasting
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ farmer
│  │  ├─ farmer-dashboard
│  │  │  ├─ components
│  │  │  │  └─ FarmerDashboard.tsx
│  │  │  └─ index.ts
│  │  ├─ farmer-inventory
│  │  │  ├─ constants.ts
│  │  │  ├─ farmer-inventory.css
│  │  │  ├─ FarmerInventory.tsx
│  │  │  ├─ hooks.ts
│  │  │  ├─ index.ts
│  │  │  ├─ services.ts
│  │  │  └─ types.ts
│  │  ├─ feature-directory
│  │  │  ├─ feature-directory.css
│  │  │  ├─ FeatureDirectory.tsx
│  │  │  └─ index.ts
│  │  ├─ impact
│  │  ├─ index.ts
│  │  ├─ logistics
│  │  ├─ market-insights
│  │  │  ├─ index.ts
│  │  │  ├─ market-insights.css
│  │  │  ├─ MarketInsights.tsx
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ marketplace
│  │  ├─ notifications
│  │  │  ├─ index.ts
│  │  │  ├─ NotificationCenter.tsx
│  │  │  ├─ notifications.css
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ order-tracking
│  │  │  ├─ constants.ts
│  │  │  ├─ hooks.ts
│  │  │  ├─ index.ts
│  │  │  ├─ order-tracking.css
│  │  │  ├─ OrderTrackingPanel.tsx
│  │  │  ├─ services.ts
│  │  │  └─ types.ts
│  │  ├─ orders
│  │  ├─ portal
│  │  │  └─ DashboardPortal.tsx
│  │  ├─ price-intelligence
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  ├─ product-reviews
│  │  │  ├─ index.ts
│  │  │  ├─ product-reviews.css
│  │  │  ├─ ProductReviews.tsx
│  │  │  ├─ service.ts
│  │  │  └─ types.ts
│  │  ├─ profile-account
│  │  │  ├─ index.ts
│  │  │  ├─ profile-account.css
│  │  │  └─ ProfileAccount.tsx
│  │  ├─ route-optimization
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  ├─ types
│  │  │  └─ utils
│  │  ├─ supply-chain
│  │  │  ├─ components
│  │  │  ├─ constants
│  │  │  ├─ hooks
│  │  │  ├─ services
│  │  │  └─ types
│  │  └─ workflow-suite
│  │     ├─ index.ts
│  │     ├─ workflow-suite.css
│  │     └─ WorkflowWorkspace.tsx
│  ├─ hooks
│  ├─ index.css
│  ├─ layouts
│  │  ├─ index.ts
│  │  ├─ PageLayout.tsx
│  │  └─ README.md
│  ├─ lib
│  ├─ main.tsx
│  ├─ mock
│  │  ├─ buyers.ts
│  │  ├─ data
│  │  ├─ farmers.ts
│  │  ├─ forecasts.ts
│  │  ├─ notifications.ts
│  │  ├─ orders.ts
│  │  ├─ products.ts
│  │  ├─ shipments.ts
│  │  └─ users.ts
│  ├─ pages
│  │  ├─ index.ts
│  │  ├─ MarketplacePage.tsx
│  │  └─ README.md
│  ├─ services
│  │  ├─ aiService.ts
│  │  ├─ analyticsService.ts
│  │  ├─ authService.ts
│  │  ├─ buyerService.ts
│  │  ├─ farmerService.ts
│  │  ├─ logisticsService.ts
│  │  ├─ notificationService.ts
│  │  ├─ orderService.ts
│  │  ├─ paymentService.ts
│  │  └─ productService.ts
│  ├─ store
│  │  ├─ authStore.ts
│  │  ├─ cartStore.ts
│  │  └─ slices
│  ├─ types
│  │  └─ api.ts
│  └─ utils
│     └─ storage.ts
├─ tsconfig.app.json
├─ tsconfig.json
├─ tsconfig.node.json
└─ vite.config.ts

```