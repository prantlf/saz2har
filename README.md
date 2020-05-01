# @prantlf/saz2har

[![NPM version](https://badge.fury.io/js/%40prantlf%2Fsaz2har.svg)](http://badge.fury.io/js/%40prantlf%2Fsaz2har)
[![Dependency Status](https://david-dm.org/prantlf/saz2har.svg)](https://david-dm.org/prantlf/saz2har)
[![devDependency Status](https://david-dm.org/prantlf/saz2har/dev-status.svg)](https://david-dm.org/prantlf/saz2har#info=devDependencies)

Converts SAZ file (from Fiddler) to HAR file (for Chrome).

This fork of the original project includes the following enhancements:

* Runs on OSX. (Replaced `minizip` with `extract-zip`.)
* The HAR validation can be disabled. (The current validator does not handle date-time values in some Fiddler logs well.)
* The command-like tool is documented and prints usage instructions.
* The dependencies are upgraded to the the most recent versions.

## Installation

Make sure that you use Node.js 6 or newer. Install this package locally if you want to use it programmatically:

```
$ npm i @prantlf/saz2har
```

If you want to use the command-line tool, install the package globally:

```
$ npm i -g @prantlf/saz2har
```

## API

### convert(input, [output], [options])

* `input` - path to the input .saz file
* `output` - path to the output .har file
* `options` - object with conversion options
  * `validate` - enables validation of the the HAR output (default: `true`)

```js
const saz2har = require("@prantlf/saz2har");

saz2har.convert("tmp/log.saz", (err, data) => {
    if (err) {
        return console.error(err);
    }
    console.log(data);
});
```

## Tool

```
$ saz2har --help

Usage: saz2har [options] input.saz [output.har]

Options:
  --help         Show help                                     [boolean]
  --version      Show version                                  [boolean]
  --no-validate  Validate the output HAR file (default: true)  [boolean]

Examples:
  saz2har foo.saz bar.har --no-validate
```

## License

MIT
