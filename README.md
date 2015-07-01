# Este (Blueberry fork)

## Techniques

- Isomorphic pure [React](http://facebook.github.io/react/) with server side rendering on [expressjs](http://expressjs.com/) backend.
- Stateless vanilla [Flux](https://facebook.github.io/flux/) with atomic global immutable app state like [Om](https://github.com/omcljs/om) via [immutable.js](http://facebook.github.io/immutable-js) for super fast rendering and sane state management.
- Functional design. Class is a leaky abstraction for "business model".
- ECMAScript 2015+ with the best transpiler [babeljs.io](https://babeljs.io/). [JSX](http://facebook.github.io/react/docs/jsx-in-depth.html) and [Flowtype](http://flowtype.org/) syntax supported. Sourcemaps are enabled by default.
- Well tuned webpack dev stack with handy [notifier](https://github.com/mikaelbr/node-notifier).
- CSS livereload.
- Hot module reload for React components and Flux actions and stores..
- [Karma](http://karma-runner.github.io/) as the test runner, [mocha](http://mochajs.org/) as test framework, and [Chai](http://chaijs.com/) as BDD / TDD assertion library.
- Testing stack configured for TDD - test driven development.
- [Shallow rendering](https://facebook.github.io/react/docs/test-utils.html#shallow-rendering) for testing React components without DOM.
- [eslint](http://eslint.org/) ES6 linting with [React](https://github.com/yannickcr/eslint-plugin-react) JSX support. ([Sublime Text 3 integration](https://github.com/steida/este/wiki/Recommended-Sublime-Text-3-settings#how-to-setup-the-eslint-for-st3))
- Localization via [formatjs.io](http://formatjs.io/), stale browsers supported as well.
- [react-router](https://github.com/rackt/react-router) for routing on client and server side.
- Simple yet powerfull sync/async validation based on famous [chriso/validator.js](https://github.com/chriso/validator.js)
- Login and Signup, `requireAuth` [higher order](https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750) component to protect access to specific pages.
- LESS, SASS, Stylus, or plain CSS with [autoprefixer](https://github.com/postcss/autoprefixer).
- Easy undo/redo and load/save for app state.

## Prerequisites

Install [node.js](http://nodejs.org).
Then install [gulp.js](http://gulpjs.com/).
```shell
npm install -g gulp
```

## Create App

```shell
git clone https://github.com/blueberryapps/este.git este-app
cd este-app
npm install
```

## Start Development

- run `gulp`
- point your browser to [localhost:8000](http://localhost:8000)

## Dev Tasks

- `gulp` run app in development mode
- `gulp -p` run app in production mode
- `gulp test`
- `gulp fontIcons` generate font icons from SVGs
- `gulp browserList` generate list of supported browsers

## CI Tasks

- `npm start` just run app, remember to set NODE_ENV=production and others environment variables.
- `npm postinstall` just alias for `gulp build --production`, useful for Heroku.
- `npm test` just alias for `gulp test`

## Documentation

So you decided to give a chance to this web stack, but where is documentation? Code is documentation itself as it illustrates various patterns, but for start you should read something about [React.js](http://facebook.github.io/react/). Then you should learn [what is the Flux
application architecture](https://medium.com/brigade-engineering/what-is-the-flux-application-architecture-b57ebca85b9e). Now refresh you JavaScript knowledge about "new" JavaScript - [learn ES6](https://babeljs.io/docs/learn-es6/). This stack uses [immutable.js](http://facebook.github.io/immutable-js/) and class-less design for a [good reason](https://github.com/facebook/immutable-js/#the-case-for-immutability). Check this nice short [video](https://www.youtube.com/watch?v=5yHFTN-_mOo), wouldn't be possible with classic OOP classes everywhere approach. Functional programming is a next (current) big thing, read [why](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd). [Express.js](http://expressjs.com/) is used on the [Node.js](http://nodejs.org/api/) based server. Application is [isomorphic](http://isomorphic.net/javascript), so we can share code between client and server easily. Congrats, now you're Este.js expert level 1 :-)

## Links

- [wiki: Recommended React Components](https://github.com/steida/este/wiki/Recommended-React-Components)
- [wiki: Recommended Sublime Text 3 Packages](https://github.com/steida/este/wiki/Recommended-Sublime-Text-3-settings)
- [twitter.com/estejs](https://twitter.com/estejs)
- [github.com/enaqx/awesome-react](https://github.com/enaqx/awesome-react)

## Tips and Tricks 

- To check app state, press `ctrl+shift+s`, and then open console. 
- To check app render time, open console, and write `este.measureRender = true`.
- With global app state, we don't need IoC container so badly - [SOLID: the next step is Functional](http://blog.ploeh.dk/2014/03/10/solid-the-next-step-is-functional). Still DI is relevant for some cases and then use [Pure DI](http://blog.ploeh.dk/2014/06/10/pure-di/).
- Use `const` by default, `let` if you have to rebind a variable.
- Learn and use immutable [Seq](https://github.com/facebook/immutable-js#lazy-seq). Very handy for native arrays and objects. For example, get object values: `Seq(RoomType).toSet().toJS()`
- Even though we can use `import {canUseDOM} from 'react/lib/ExecutionEnvironment'` to detect browser/server, don't do it since it's runtime value. Use webpack DefinePlugin to set `process.env.IS_BROWSER` rather, because compilation removes dead code.
- How to use Closure Tools, [gist](https://gist.github.com/steida/afbc595a1e2f27e925d9)
- Recommended editor is [sublimetext](http://www.sublimetext.com/), or [atom.io](https://atom.io) ([tips](https://github.com/steida/atom-io-settings)).
