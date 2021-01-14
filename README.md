# eslint-config-with-prettier

These are my default ESLint and Prettier settings ⚡️

Based on [`Upstatement`](https://github.com/Upstatement)'s  [`ESLint`](https://eslint.org/) and [`prettier`](https://prettier.io) configurations.

Check their documentation on  [`Prettier configuration`](https://www.npmjs.com/package/@upstatement/prettier-config) and  [`ESLint configuration`](https://www.npmjs.com/package/@upstatement/eslint-config).

## Installation

1. We need to install everything needed by the config:

```sh
# using npx

npx install-peerdeps --dev @ryuuto829/eslint-config-with-prettier

# OR using npm

npm install --save-dev @ryuuto829/eslint-config-with-prettier eslint babel-eslint prettier eslint-config-prettier

# OR using yarn

yarn add --dev @ryuuto829/eslint-config-with-prettier eslint babel-eslint prettier eslint-config-prettier
```

2. Create an `.eslintrc` file at the root of your project with the following:

```json
{
  "extends": ["@ryuuto829/eslint-config-with-prettier"]
}
```

3. Create a `prettier.config.js` file at the root of your project that contains:

```js
module.exports = require('@ryuuto829/eslint-config-with-prettier/prettier');
```

4. (Optional) Add `.editorconfig` file to the root of the project:

```pl
# http://EditorConfig.org

# Top-most EditorConfig file
root = true

# Global
[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

5. (Optional) You can add two scripts to your `package.json` to lint and/or fix:

```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix"
},
```

## Using with React

1. Install additional  dependencies:

```sh
# If project includes deafult config

yarn add --dev eslint-plugin-react eslint-plugin-jsx-a11y

# OR initiate empty project with react config

yarn add --dev @ryuuto829/eslint-config-with-prettier eslint babel-eslint prettier eslint-config-prettier eslint-plugin-react eslint-plugin-jsx-a11y
```

2. Create an `.eslintrc` file at the root of your project with the following:

```json
{
  "extends": ["@ryuuto829/eslint-config-with-prettier/react"]
}
```

## Pre-commit Hook

You can use [`lint-staged`](https://github.com/okonet/lint-staged) with [`husky`](https://github.com/typicode/husky), which manages git hooks and automatically fix your errors on commit.

1. Install

```sh
`yarn add --dev lint-staged husky`
```

2. Update your `package.json` like this:

```json
"husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,jsx,ts,tsx,css,json,md}": [
      "prettier --write"
    ],
    "*.js": [
      "eslint --fix"
    ]
  }
```

## Integration with Visual Studio Code

1. Install Prettier extension: `View → Extensions` then find and install Prettier - Code formatter.
2. Install the ESLint extension: `View → Extensions` then find and install ESLint.
3. Reload the editor.
3. In your user settings:

```js
// Format on save with Prettier rules
"editor.formatOnSave": true,
// Tell the ESLint plugin to run on save
"eslint.autoFixOnSave": true,
```
