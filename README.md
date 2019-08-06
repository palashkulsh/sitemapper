## Sitemap-parser
[![Build Status](https://travis-ci.org/hawaiianchimp/sitemapper.svg?branch=master)](https://travis-ci.org/hawaiianchimp/sitemapper) [![Monthly Downloads](https://img.shields.io/npm/dm/sitemapper.svg)](https://www.npmjs.com/package/sitemapper)
[![npm version](https://badge.fury.io/js/sitemapper.svg)](https://badge.fury.io/js/sitemapper)
[![dependencies Status](https://david-dm.org/hawaiianchimp/sitemapper/status.svg)](https://david-dm.org/hawaiianchimp/sitemapper)
[![Inline docs](http://inch-ci.org/github/hawaiianchimp/sitemapper.svg?branch=master)](http://inch-ci.org/github/hawaiianchimp/sitemapper)

Parse through a sitemaps xml to get all the urls for your crawler.
## Version 2

### Installation
```bash
npm install sitemapper --save
```

### Simple Example
```javascript
var Sitemapper = require('sitemapper');

var sitemap = new Sitemapper();

sitemap.fetch('http://wp.seantburke.com/sitemap.xml').then(function(sites) {
  console.log(sites);
});

```

### Examples in ES5
```javascript
var Sitemapper = require('sitemapper');

var Google = new Sitemapper({
  url: 'https://www.google.com/work/sitemap.xml',
  timeout: 15000, //15 seconds
  concurrentLimit: 7 //max 7 requests are allowed in parallel, defaults to 7
});

Google.fetch()
  .then(function (data) {
    console.log(data);
  })
  .catch(function (error) {
    console.log(error);
  });


// or


var sitemapper = new Sitemapper();

sitemapper.timeout = 5000;
sitemapper.concurrentLimit = 7;
sitemapper.fetch('http://wp.seantburke.com/sitemap.xml')
  .then(function (data) {
    console.log(data);
  })
  .catch(function (error) {
    console.log(error);
  });

```

### Examples in ES6
```javascript
import Sitemapper from 'sitemapper';

const Google = new Sitemapper({
  url: 'https://www.google.com/work/sitemap.xml',
  timeout: 15000, // 15 seconds
  concurrentLimit: 7, //max 7 inflight parallel requests are allowed.
});

Google.fetch()
  .then(data => console.log(data.sites))
  .catch(error => console.log(error));


// or


const sitemapper = new Sitemapper();
sitemapper.timeout = 5000;
sitemapper.concurrentLimit = 7;

sitemapper.fetch('http://wp.seantburke.com/sitemap.xml')
  .then(({ url, sites }) => console.log(`url:${url}`, 'sites:', sites))
  .catch(error => console.log(error));
```

## Version 1

```bash
npm install sitemapper@1.1.1 --save
```

### Simple Example

```javascript
var Sitemapper = require('sitemapper');

var sitemapper = new Sitemapper();

sitemapper.getSites('http://wp.seantburke.com/sitemap.xml', function(err, sites) {
    if (!err) {
     console.log(sites);
    }
});
```
