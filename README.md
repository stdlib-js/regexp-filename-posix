<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# Filename

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] [![dependencies][dependencies-image]][dependencies-url]

> [Regular expression][mdn-regexp] to split a [POSIX][posix] filename.

<section class="installation">

## Installation

```bash
npm install @stdlib/regexp-filename-posix
```

</section>

<section class="usage">

## Usage

```javascript
var reFilenamePosix = require( '@stdlib/regexp-filename-posix' );
```

#### reFilenamePosix()

Returns a [regular expression][mdn-regexp] to split a [POSIX][posix] filename.

```javascript
var RE_FILENAME_POSIX = reFilenamePosix();
var parts = RE_FILENAME_POSIX.exec( '/foo/bar/index.js' ).slice();
/* returns
    [
        '/foo/bar/index.js',  // input value
        '/',                  // root
        'foo/bar/',           // dirname
        'index.js',           // basename
        '.js'                 // extname
    ]
*/
```

#### reFilenamePosix.REGEXP

[Regular expression][mdn-regexp] to split a [POSIX][posix] filename.

```javascript
var parts = reFilenamePosix.REGEXP.exec( '/foo/bar/index.js' ).slice();
/* returns
    [
        '/foo/bar/index.js',  // input value
        '/',                  // root
        'foo/bar/',           // dirname
        'index.js',           // basename
        '.js'                 // extname
    ]
*/
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   When executed against dotfile filenames (e.g., `.gitignore`), the [regular expression][mdn-regexp] does **not** capture the basename as a filename extension.

    ```javascript
    var parts = reFilenamePosix.REGEXP.exec( '.bash_profile' ).slice();
    /* returns
      [
          '.bash_profile',
          '',
          '',
          '.bash_profile',
          ''
      ]
    */

    parts = reFilenamePosix.REGEXP.exec( '.travis.yml' ).slice();
    /* returns
      [
          '.travis.yml',
          '',
          '',
          '.travis.yml',
          '.yml'
      ]
    */
    ```

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var reFilenamePosix = require( '@stdlib/regexp-filename-posix' );

var RE_FILENAME_POSIX = reFilenamePosix();
var parts = RE_FILENAME_POSIX.exec( 'index.js' ).slice();
/* returns
    [
        'index.js',
        '',
        '',
        'index.js',
        '.js'
    ]
*/

parts = RE_FILENAME_POSIX.exec( '/foo/bar/home.html' ).slice();
/* returns
    [
        '/foo/bar/home.html',
        '/',
        'foo/bar/',
        'home.html',
        '.html'
    ]
*/

parts = RE_FILENAME_POSIX.exec( 'foo/file.pdf' ).slice();
/* returns
    [
        'foo/file.pdf',
        '',
        'foo/',
        'file.pdf',
        '.pdf'
    ]
*/

parts = RE_FILENAME_POSIX.exec( 'beep/boop.' ).slice();
/* returns
    [
        'beep/boop.',
        '',
        'beep/',
        'boop.',
        '.'
    ]
*/

parts = RE_FILENAME_POSIX.exec( '' ).slice();
/* returns
    [
        '',
        '',
        '',
        '',
        ''
    ]
*/

parts = RE_FILENAME_POSIX.exec( '/foo/bar/file' ).slice();
/* returns
    [
        '/foo/bar/file',
        '/',
        'foo/bar/',
        'file',
        ''
    ]
*/

parts = RE_FILENAME_POSIX.exec( '/foo/bar/.gitignore' ).slice();
/* returns
    [
        '/foo/bar/.gitignore',
        '/',
        'foo/bar/',
        '.gitignore',
        ''
    ]
*/
```

</section>

<!-- /.examples -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/regexp-filename-posix.svg
[npm-url]: https://npmjs.org/package/@stdlib/regexp-filename-posix

[test-image]: https://github.com/stdlib-js/regexp-filename-posix/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/regexp-filename-posix/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/regexp-filename-posix/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/regexp-filename-posix?branch=main

[dependencies-image]: https://img.shields.io/david/stdlib-js/regexp-filename-posix
[dependencies-url]: https://david-dm.org/stdlib-js/regexp-filename-posix/main

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/regexp-filename-posix/main/LICENSE

[mdn-regexp]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

[posix]: https://en.wikipedia.org/wiki/POSIX

</section>

<!-- /.links -->
