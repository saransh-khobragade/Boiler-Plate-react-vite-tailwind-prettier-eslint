# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

## 🚀 Quick Start

```bash
# Install dependencies
yarn install

# Start development server
yarn dev

# Build for production
yarn build

# Run linting
yarn lint

# Fix linting issues
yarn lint:fix

# Format code
yarn format
```

## 🔧 ESLint on Save Setup

This project is configured to show ESLint errors and warnings on save in VS Code with **STRICT** linting rules. The setup includes:

### Required VS Code Extensions

- **ESLint** (`dbaeumer.vscode-eslint`) - For ESLint integration
- **Prettier** (`esbenp.prettier-vscode`) - For code formatting
- **TypeScript** (`ms-vscode.vscode-typescript-next`) - For TypeScript support
- **Tailwind CSS** (`bradlc.vscode-tailwindcss`) - For Tailwind CSS IntelliSense

### Features

- ✅ **STRICT** ESLint errors and warnings shown in real-time
- ✅ Auto-fix on save for ESLint issues
- ✅ Prettier formatting on save
- ✅ TypeScript IntelliSense and error checking
- ✅ Conventional commit message validation
- ✅ Pre-commit hooks for linting and formatting

### 🚨 Strict ESLint Rules

#### TypeScript Strict Rules

- `@typescript-eslint/no-explicit-any` - Bans `any` type usage
- `@typescript-eslint/no-non-null-assertion` - Bans `!` non-null assertions
- `@typescript-eslint/no-unsafe-*` - Bans unsafe TypeScript operations
- `@typescript-eslint/prefer-nullish-coalescing` - Enforces `??` over `||`
- `@typescript-eslint/prefer-optional-chain` - Enforces `?.` over `&&`
- `@typescript-eslint/consistent-type-imports` - Enforces consistent import types
- `@typescript-eslint/no-floating-promises` - Bans unhandled promises
- `@typescript-eslint/await-thenable` - Enforces proper async/await usage

#### JavaScript Strict Rules

- `no-console` - **ERROR**: Bans console statements
- `no-debugger` - **ERROR**: Bans debugger statements
- `no-eval` - **ERROR**: Bans eval usage
- `no-var` - **ERROR**: Bans var declarations
- `prefer-const` - **ERROR**: Enforces const over let
- `no-duplicate-imports` - **ERROR**: Bans duplicate imports
- `prefer-template` - **ERROR**: Enforces template literals
- `object-shorthand` - **ERROR**: Enforces object shorthand
- `prefer-destructuring` - **ERROR**: Enforces destructuring

#### React Strict Rules

- `react-hooks/rules-of-hooks` - **ERROR**: Enforces hooks rules
- `react-hooks/exhaustive-deps` - **ERROR**: Enforces complete dependencies

#### Code Style Rules

- `sort-imports` - **ERROR**: Enforces alphabetical import sorting
- `quotes` - **ERROR**: Enforces single quotes
- `semi` - **ERROR**: Enforces semicolons
- `comma-dangle` - **ERROR**: Enforces trailing commas
- `indent` - **ERROR**: Enforces 2-space indentation
- `space-before-function-paren` - **ERROR**: Enforces function spacing
- `object-curly-spacing` - **ERROR**: Enforces object spacing
- `array-bracket-spacing` - **ERROR**: Enforces array spacing

### VS Code Settings

The `.vscode/settings.json` file configures:

- ESLint validation for TypeScript and React files
- Auto-fix on save for ESLint issues
- Prettier as the default formatter
- Format on save enabled

## 📝 Git Hooks

This project uses Husky for Git hooks:

- **Pre-commit**: Runs lint-staged to format and lint staged files
- **Commit-msg**: Validates commit messages follow conventional format

Valid commit message formats:

- `feat: add new feature`
- `fix: resolve bug`
- `docs: update documentation`
- `style: formatting changes`
- `refactor: code refactoring`
- `test: add tests`
- `chore: maintenance tasks`

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

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
]);
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x';
import reactDom from 'eslint-plugin-react-dom';

export default tseslint.config([
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
]);
```
