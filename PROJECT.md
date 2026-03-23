# Monorepo Project Guide (Turborepo + pnpm)

## 🏗 Directory Structure
- `apps/web`: Next.js (Frontend) - Main user interface.
- `packages/ui`: React Component Library - Shared UI elements (Buttons, Cards, etc.).
- `packages/tailwind-config`: Shared Tailwind CSS theme and settings.
- `packages/tsconfig`: Shared TypeScript configurations.

## 🛠 Critical Commands
- **Install dependencies:** `pnpm install`
- **Run all apps in dev:** `pnpm dev`
- **Build all projects:** `pnpm build`
- **Lint everything:** `pnpm lint`
- **Add a new dependency to a specific app:** `pnpm add <pkg> --filter <app-name>`

## 📝 Development Rules
1. **Internal Imports:** Use the `@repo/` prefix for all shared packages (e.g., `import { Button } from "@repo/ui"`).
2. **New Components:** Always create UI components in `packages/ui` first, then import them into `apps/web`.
3. **Styling:** Use Tailwind CSS utility classes. If a new color or theme change is needed, update `packages/tailwind-config/tailwind.config.js`.
4. **Type Safety:** Ensure all shared components have explicit TypeScript interfaces.
5. **No Direct NPM:** Never use `npm` or `yarn`. Only use `pnpm` to maintain the `pnpm-lock.yaml`.

## 🔗 Connection Map
- `apps/web` depends on `@repo/ui` and `@repo/tailwind-config`.
- `packages/ui` depends on `@repo/tailwind-config`.
- When modifying `packages/ui`, you must check if `apps/web` needs a restart or if `turbo` handles the hot-reload.