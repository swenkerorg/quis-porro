# @swenkerorg/quis-porro <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Is this value a JS SharedArrayBuffer? This module works cross-realm/iframe, does not depend on `instanceof` or mutable properties, and despite ES6 Symbol.toStringTag.

## Example

```js
var assert = require('assert');
var isSharedArrayBuffer = require('@swenkerorg/quis-porro');

assert(!isSharedArrayBuffer(function () {}));
assert(!isSharedArrayBuffer(null));
assert(!isSharedArrayBuffer(function* () { yield 42; return Infinity; });
assert(!isSharedArrayBuffer(Symbol('foo')));
assert(!isSharedArrayBuffer(1n));
assert(!isSharedArrayBuffer(Object(1n)));

assert(!isSharedArrayBuffer(new Set()));
assert(!isSharedArrayBuffer(new WeakSet()));
assert(!isSharedArrayBuffer(new Map()));
assert(!isSharedArrayBuffer(new WeakMap()));
assert(!isSharedArrayBuffer(new WeakRef({})));
assert(!isSharedArrayBuffer(new FinalizationRegistry(() => {})));
assert(!isSharedArrayBuffer(new ArrayBuffer()));

assert(isSharedArrayBuffer(new SharedArrayBuffer()));

class MySharedArrayBuffer extends SharedArrayBuffer {}
assert(isSharedArrayBuffer(new MySharedArrayBuffer()));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@swenkerorg/quis-porro
[npm-version-svg]: https://versionbadg.es/inspect-js/@swenkerorg/quis-porro.svg
[deps-svg]: https://david-dm.org/inspect-js/@swenkerorg/quis-porro.svg
[deps-url]: https://david-dm.org/inspect-js/@swenkerorg/quis-porro
[dev-deps-svg]: https://david-dm.org/inspect-js/@swenkerorg/quis-porro/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@swenkerorg/quis-porro#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@swenkerorg/quis-porro.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@swenkerorg/quis-porro.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@swenkerorg/quis-porro.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@swenkerorg/quis-porro
[codecov-image]: https://codecov.io/gh/inspect-js/@swenkerorg/quis-porro/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@swenkerorg/quis-porro/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@swenkerorg/quis-porro
[actions-url]: https://github.com/swenkerorg/quis-porro/actions
