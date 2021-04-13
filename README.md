# R&D on using StandardJS

[![forthebadge](https://forthebadge.com/images/badges/makes-people-smile.svg)](https://forthebadge.com)
[![npm](https://badgen.net/badge/icon/npm?icon=npm&label)](https://badgen.net/badge/icon/npm?icon=npm&label)
[![vscode](https://badgen.net/badge/icon/visualstudio?icon=visualstudio&label)](https://badgen.net/badge/icon/visualstudio?icon=visualstudio&label)

The goal behind this R&D session was to see if StandardJS, ESLint and Prettier can play together, but why ?

StandardJS is available as a plugin for VSCode and it allows formatting on save.
For the linter part, you have to install a npm package, so 2 different things. And what happens if I change my computer of a new mate comes in the team or if i work with a contractor who works on multiple projects for companies who does not use the same rules ?

Maybe we can enforce the usage of StandardJS per project and not globally from the IDE.

## ESLint

ESLint is by far the most popular Javascript Linter. According to your set of rules, it helps you find code inconsitencies but do not format your code according to your coding styles guide.

## Prettier

Prettier is a code formatter. Unlike ESLint it doesn't check your code for inconsistencies, it just formats your code according to the rules you have defined.

## EditorConfig

### What is EditorConfig

From EditorConfig itself:

> EditorConfig helps maintain consistent coding styles for multiple developers working on the same project across various editors and IDEs.

You don't have to explicitly set any rules in your IDE settings. A single .editorconfig at the root of your project and your mostly done.

Unlike Prettier that formats your code, EditorConfig enforce the coding styles to follow for your project once you start a new file, and not on saving it.

### What are the rules supported

EditorConfig does not deal with comma, semicolons, etc ....

It focuses on:

- indent_style: tab, space
- indent_size: an integer or tab
- tab_width: integer
- end_of_line: lf, crlf, cr
- charset: latin1, utf-8, ...
- trim_trailing_whitespace: boolean
- insert_final_newline: boolean
- max_line_length: integer or off (not supported by every browsers)

### How do i use it ?

On VSCode, install this plugin: https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig

On Webstorm, install this plugin: https://plugins.jetbrains.com/plugin/7294-editorconfig

## StandardJS

### What is StandardJS

StandardJS is a style guide, a formatter and a linter.

### Is it an official standard ?

No, it's not a real standard approved by W3C for example but is there any ? Not realy, each company as its own rules for linting, formatting and coding style.

### Why should i use it ?

For 2 main reasons:

1. You don't have to maintain a long, very long set of rules that are discussed during boring and neverending meetings.

2. StandardJS is supported by great projects and companies like:

- NodeJS itself
- NPM
- ExpressJS
- Elastic
- and more on the official Website

### Some rules

- only camelCase for variables names
- avoid dual import
- no semicolon
- no trailing comma

### StandardJS says no to semicolons

Yes, and they're right. Semicolons are infered by the Javascript engine. If don't put one in your code the engine will set it for you. This is part of the ASI (Automatic Semicolon Insertion).

You can find more explanations by Codeburst.io [here](https://codeburst.io/ecmascript-automatic-semicolon-insertion-50f09091e377).

## Setup

### Typescript

1. install this packages as dev dependencies

- eslint >= 7.15.0
- eslint-plugin-promise
- eslint-plugin-import
- eslint-plugin-node
- @typescript-eslint/eslint-plugin
- @typescript-eslint/parser
- eslint-config-standard
- prettier-config-standard

```sh
npm install --save-dev --save-exact eslint eslint-plugin-promise eslint-plugin-import eslint-plugin-node @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-standard prettier-config-standard
```

2. Add these lines to your package.json

```javascript
"src:build": "npm run lint && tsc",
"src:watch": "npm run lint && tsc -w",
"lint": "eslint . --ext .js,.ts",
"lint:fix": "eslint . --ext .js,.ts --fix"
```

3. Copy/paste the src/.editorconfig at the root of your repo

4. Copy/paste the files in src/typescript of this repo

### VueJS

1. install this packages

```sh
npm install --save-dev --save-exact eslint eslint-plugin-promise eslint-plugin-import eslint-plugin-node @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-standard prettier-config-standard @vue/eslint-config-standard
```

2. Add these lines to your package.json

```javascript
"lint": "eslint . --ext .js,.ts,.vue",
```

3. Copy/paste the src/.editorconfig at the root of your repo

4. Copy/paste the files in src/vue of this repo

## Troubleshooting

### Error: Environment key "es2021" is unknown

This error may throw if your repo use and old version of eslint. Please upgrade it to 7.15.0+.

## Sources

[StandardJS - Official Web site](https://standardjs.com/)

[EditorConfig - Official Web site](https://editorconfig.org/)

[Why The Heck Do I Need To Use Semi-Colons in Javascript](https://code.likeagirl.io/why-the-heck-do-i-need-to-use-semi-colons-in-javascript-4f8712c82329)

[ECMAScript Automatic Semicolon Insertion by Codeburst](https://codeburst.io/ecmascript-automatic-semicolon-insertion-50f09091e377)

---

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)
