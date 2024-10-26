<p align="center">
  <img src="https://konvajs.org/android-chrome-192x192.png" alt="Konva logo" height="180" />
</p>

<h1 align="center">Konva</h1>

[![npm version](https://badge.fury.io/js/konva.svg)](http://badge.fury.io/js/konva)
[![Build Status](https://github.com/konvajs/konva/actions/workflows/test-browser.yml/badge.svg)](https://github.com/konvajs/konva/actions/workflows/test-browser.ym)
[![Build Status](https://github.com/konvajs/konva/actions/workflows/test-node.yml/badge.svg)](https://github.com/konvajs/konva/actions/workflows/test-node.ym)[![CDNJS version](https://img.shields.io/cdnjs/v/konva.svg)](https://cdnjs.com/libraries/konva)

Konva is an HTML5 Canvas JavaScript framework that enables high performance animations, transitions, node nesting, layering, filtering, caching, event handling for desktop and mobile applications, and much more.

You can draw things onto the stage, add event listeners to them, move them, scale them, and rotate them independently from other shapes to support high performance animations, even if your application uses thousands of shapes. Served hot with a side of awesomeness.

This repository began as a GitHub fork of [konva/konvajs](https://github.com/konva/konvajs).

- **Visit:** The [Home Page](http://konvajs.org/) and follow on [Twitter](https://twitter.com/lavrton)
- **Discover:** [Tutorials](http://konvajs.org/docs), [API Documentation](http://konvajs.org/api)
- **Help:** [StackOverflow](http://stackoverflow.com/questions/tagged/konvajs), [Discord Chat](https://discord.gg/8FqZwVT)

# Quick Look

```html
<script src="https://unpkg.com/konva@9/konva.min.js"></script>
<div id="container"></div>
<script>
  var stage = new Konva.Stage({
    container: 'container',
    width: window.innerWidth,
    height: window.innerHeight,
  });

  // add canvas element
  var layer = new Konva.Layer();
  stage.add(layer);

  // create shape
  var box = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 50,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4,
    draggable: true,
  });
  layer.add(box);

  // add cursor styling
  box.on('mouseover', function () {
    document.body.style.cursor = 'pointer';
  });
  box.on('mouseout', function () {
    document.body.style.cursor = 'default';
  });
</script>
```

# Browsers support

Konva works in all modern mobile and desktop browsers. A browser need to be capable to run javascript code from ES2015 spec. For older browsers you may need polyfills for missing functions.

At the current moment `Konva` doesn't work in IE11 directly. To make it work you just need to provide some polyfills such as `Array.prototype.find`, `String.prototype.trimLeft`, `String.prototype.trimRight`, `Array.from`.

# Debugging

The Chrome inspector simply shows the canvas element.  To see the Konva objects and their details, install the konva-dev extension at https://github.com/konvajs/konva-devtool.

# Loading and installing Konva

Konva supports UMD loading. So you can use all possible variants to load the framework into your project:

### Load Konva via classical `<script>` tag from CDN:

```html
<script src="https://unpkg.com/konva@9/konva.min.js"></script>
```

### Install with npm:

```bash
npm install konva --save
```

```javascript
// The modern way (e.g. an ES6-style import for webpack, parcel)
import Konva from 'konva';
```

#### Typescript usage

Add DOM definitions into your `tsconfig.json`:

```
{
  "compilerOptions": {
    "lib": [
        "es6",
        "dom"
    ]
  }
}
```

### 3 Minimal bundle

```javascript
import Konva from 'konva/lib/Core';
// Now you have a Konva object with Stage, Layer, FastLayer, Group, Shape and some additional utils function.
// Also core currently already have support for drag&drop and animations.
// BUT there are no shapes (rect, circle, etc), no filters.

// but you can simply add anything you need:
import { Rect } from 'konva/lib/shapes/Rect';
// importing a shape will automatically inject it into Konva object

var rect1 = new Rect();
// or:
var shape = new Konva.Rect();

// for filters you can use this:
import { Blur } from 'konva/lib/filters/Blur';
```

### 4 NodeJS env

In order to run `konva` in nodejs environment you also need to install `canvas` package manually. Konva will use it for 2d canvas API.

```bash
npm install konva canvas
```

Then you can use the same Konva API and all Konva demos will work just fine. You just don't need to use `container` attribute in your stage.

```js
import Konva from 'konva';

const stage = new Konva.Stage({
  width: 500,
  height: 500,
});
// then all regular Konva code will work
```
# Change log

See [CHANGELOG.md](https://github.com/konvajs/konva/blob/master/CHANGELOG.md).

## Building the Konva Framework

To make a full build run `npm run build`. The command will compile all typescript files, combine then into one bundle and run minifier.

## Testing

Konva uses Mocha for testing.

- If you need run test only one time run `npm run test`.
- While developing it is easy to use `npm start`. Just run it and go to [http://localhost:1234/unit-tests.html](http://localhost:1234/unit-tests.html). The watcher will rebuild the bundle on any change.

Konva is covered with hundreds of tests and well over a thousand assertions.
Konva uses TDD (test driven development) which means that every new feature or bug fix is accompanied with at least one new test.

## Generate documentation

Run `npx gulp api` which will build the documentation files and place them in the `api` folder.

# Pull Requests

I'd be happy to review any pull requests that may better the Konva project,
in particular if you have a bug fix, enhancement, or a new shape (see `src/shapes` for examples). Before doing so, please first make sure that all of the tests pass (`npm run test`).

