# eslint-plugin-quibble

![npm latest version](https://img.shields.io/npm/v/eslint-plugin-quibble?style=for-the-badge) ![license](https://img.shields.io/npm/l/eslint-plugin-quibble?style=for-the-badge) ![downloads](https://img.shields.io/npm/dt/eslint-plugin-quibble?style=for-the-badge)

## Supported rules

Learn more about each supported rules by reading their documentation:

- `no-excessive-whitespace`: removes unnecessary whitespace characters, including leading and trailing spaces, as well as multiple spaces between class names.

By using [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) extension for Visual Studio Code, you will get the following messages:
![errors](.github/output.png)

## Latest changes

The `vue-no-excessive-whitespace` was renamed to `no-excessive-whitespace` and `{j,t}sx` support was added.

Check out the full changelog [here](CHANGELOG.md).

## Installation

### 1. Install `eslint` and `eslint-plugin-quibble`

```
pnpm i -D eslint eslint-plugin-quibble
```

### 2. Extend eslint configuration and enable rules

- (Optional) Install Vue parser: `pnpm i -D vue-eslint-parser`

- Inside your `eslint.config.js`:

```js
import quibble from 'eslint-plugin-quibble'

export default [
  {
    plugins: {
      quibble
    },

    rules: {
      'quibble/no-excessive-whitespace': 'error'
    },
  },
  {
    files: ['*.vue'],
    languageOptions: {
      parser: 'vue-eslint-parser',
    }
  },
]
```

Adding `vue-eslint-parser` is optional - some popular configs such as [`antfu/eslint-config`](https://github.com/antfu/eslint-config) have it installed and configured already.

## Future

In the future, this plugin will be expanded by the rules the community or myself find worth of adding.

## FAQ

### Quibble?

**To argue about, or say you disapprove of, something that is not important**:

- _There's no point quibbling about/over a couple of ~~dollars~~ whitespace characters_.

### What are your motivations?

To be perfectly honest, when doing code reviews at work, I often spot excessive whitespace characters, typos, or other stylistic errors - and it really irks me.

Should I nitpick the PR and point out those lines, saying:

> Hey, could you remove this whitespace? I know it doesn't change much, but I'd be pleased to see it gone from the codebase. :)

Well, probably not. It's **annoying to impose stylistic rules** on developers that cannot be auto-fixed by their IDE - something I've learned from Theo. That's why I've developed this ESLint plugin.

Side note: The other option, to avoid making my fellow developers angry with me, was delivering the nitpicks in the form of a meme, which I actually did (at least) once `#meme-driven-development`.

![missing-space](.github/excessive-space.jpg)

### Why a separate plugin / why not contribute to already existing projects?

There are a few reasons why. The primary one is that I wanted to finally build a tool on my own. I've spent countless hours configuring ESLint to work the way I want, and my curiosity about how it works internally eventually won.

The second reason why, it takes time to get your PR reviewed, accepted and published. Where would the `no-excessive-whitespace` rule even fit? [`eslint-plugin-perfectionist`](https://github.com/azat-io/eslint-plugin-perfectionist), [`eslint-stylistic`](https://github.com/eslint-stylistic/eslint-stylistic) or maybe [`eslint-plugin-tailwindcss`](https://github.com/francoismassart/eslint-plugin-tailwindcss/tree/master)? There's an issue opened on the last one since Jul 21, 2023.

Therefore, it was easier to create a plugin from scratch - something I have a full control of, can use right away, and can learn from in the process.

### Is the project open to contributions?

Yes! I very much welcome the community's input, and I would be pleased to see your ideas on how to expand or improve this plugin. Feel free to open an issue. :)

### Why an ESLint plugin for code formatting / why not Prettier?

Following Anthony Fu's example with [`antfu/eslint-config`](https://github.com/antfu/eslint-config), I'm migrating my projects to use only ESLint for both syntax highlighting and code formatting. Although [`prettier/eslint-plugin-prettier`](https://github.com/prettier/eslint-plugin-prettier) exists, I found it too annoying to configure both Prettier and ESLint, especially with the conflicts that can arise between the two.

### Is flat config supported?

Yes.

## Further reading

### Eslint Config Inspector

You can check out your ESLint config by using the official tool - [ESLint Config Inspector](https://github.com/eslint/config-inspector):

```
pnpm dlx @eslint/config-inspector@latest
```

## Inspirations

I was heavily inspired by [eslint-plugin-tailwindcss](https://github.com/francoismassart/eslint-plugin-tailwindcss/tree/master) and [eslint-plugin-vue](https://github.com/vuejs/eslint-plugin-vue) as the source code (structure, methods of crawling into nodes, naming conventions etc.) for those plugins was essentially my entry point and the base to creating `eslint-plugin-quibble`.
