![Build status](https://travis-ci.org/vinceallenvince/borderpalette.svg?branch=master)

# borderpalette

Randomly select border styles from a range of presets.

##Install

To include borderpalette as a component in your project, use the node module.

```
npm install borderpalette --save
```

You can also use the [standalone version](https://github.com/vinceallenvince/borderpalette/releases/latest) and reference the js file from your document.

```
<html>
  <head>
    <script src="scripts/borderpalette.min.js" type="text/javascript" charset="utf-8"></script>
  </head>
  ...
```

##Usage

The module exports a BorderPalette class. In a nodejs project, you access it via:

```
var BorderPalette = require('borderpalette');
var palette = new BorderPalette();
```

Add styles to your palette via addBorder(). Pass the min/max amounts plus the border style. The add function adds a random number between your min and max. In the example below, you are twice as likely to get a 'dotted' style from the palette. Notice you can also chain your addBorder() calls.

```
pal.addBorder({
  min: 2,
  max: 10,
  style: 'solid'
}).addBorder({
  min: 2,
  max: 20,
  style: 'dotted'
});
```

To retrieve a style from the palette, use getBorder().

```
var style = pal.getBorder();
```

In the browser, the module exposes a BorderPalette namespace.

```
<html>
  <head>
    <script src="scripts/borderpalette.min.js" type="text/javascript" charset="utf-8"></script>
  </head>
  <body>
    <script>
      var pal = new BorderPalette();
      pal.addBorder({
        min: 2,
        max: 10,
        style: 'solid'
      }).addBorder({
        min: 2,
        max: 20,
        style: 'dotted'
      });
      var box = document.createElement('div');
      box.style.cssText = 'width: 100px; height: 100px; borderWidth: 4px; borderColor: red;';
      box.style.borderStyle = pal.getBorder();
      document.body.appendChild(box);
    </script>
  </body>
</html>
```

To learn how to use the various BorderPalette functions, please review [the docs](http://vinceallenvince.github.io/borderpalette/doc/).

##Building this project

This project uses [Grunt](http://gruntjs.com). To build the project first install the node modules.

```
npm install
```

Next, run grunt.

```
grunt
```

To run the tests, run 'npm test'.

```
npm test
```

To check test coverage run 'grunt coverage'.

```
grunt coverage
```

A pre-commit hook is defined in /pre-commit that runs jshint. To use the hook, run the following:

```
ln -s ../../pre-commit .git/hooks/pre-commit
```

A post-commit hook is defined in /post-commit that runs the Plato complexity analysis tools. To use the hook, run the following:

```
ln -s ../../post-commit .git/hooks/post-commit
```

View the [code complexity](http://vinceallenvince.github.io/borderpalette/reports/) report.
