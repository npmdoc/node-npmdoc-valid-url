# api documentation for  [valid-url (v1.0.9)](https://github.com/ogt/valid-url#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-valid-url.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-valid-url) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-valid-url.svg)](https://travis-ci.org/npmdoc/node-npmdoc-valid-url)
#### URI validation functions

[![NPM](https://nodei.co/npm/valid-url.png?downloads=true)](https://www.npmjs.com/package/valid-url)

[![apidoc](https://npmdoc.github.io/node-npmdoc-valid-url/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-valid-url_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-valid-url/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-valid-url/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-valid-url/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/ogt/valid-url/issues"
    },
    "dependencies": {},
    "description": "URI validation functions",
    "devDependencies": {
        "jshint": "~2.1.4",
        "tap": "~0.4.3"
    },
    "directories": {},
    "dist": {
        "shasum": "1c14479b40f1397a75782f115e4086447433a200",
        "tarball": "https://registry.npmjs.org/valid-url/-/valid-url-1.0.9.tgz"
    },
    "homepage": "https://github.com/ogt/valid-url#readme",
    "keywords": [
        "url",
        "validation",
        "check",
        "checker",
        "pattern"
    ],
    "main": "index.js",
    "maintainers": [
        {
            "name": "odysseas",
            "email": "odysseas@tsatalos.com"
        },
        {
            "name": "sagens",
            "email": "zholudev.s@gmail.com"
        }
    ],
    "name": "valid-url",
    "optionalDependencies": {},
    "readme": "URI validation functions\n==\n[![Build Status](https://travis-ci.org/ogt/valid-url.png)](https://travis-ci.org/ogt/valid-url)\n\n## Synopsis\n\nCommon url validation methods \n'''\n    var validUrl = require('valid-url');\n  \n    if (validUrl.isUri(suspect)){\n        console.log('Looks like an URI');\n    } else {\n        console.log('Not a URI');\n    }\n'''\n\nReplicates the functionality of Richard Sonnen <sonnen@richardsonnen.com> perl module :\nhttp://search.cpan.org/~sonnen/Data-Validate-URI-0.01/lib/Data/Validate/URI.pm [full code here](http://anonscm.debian.org/gitweb/?p=users/dom/libdata-validate-uri-perl.git)\ninto a nodejs module. Translated practically line by line from perl. \nIt passes all the original tests.\n\n## Description\n\n(copied from original perl module)\n\n> This module collects common URI validation routines to make input validation, and untainting easier and more readable.\n> All functions return an untainted value if the test passes, and undef if it fails. This means that you should always check for a defined status explicitly. Don't assume the return will be true.\n> The value to test is always the first (and often only) argument.\n> There are a number of other URI validation modules out there as well (see below.) This one focuses on being fast, lightweight, and relatively 'real-world'. i.e. it's good if you want to check user input, and don't need to parse out the URI/URL into chunks.\n> Right now the module focuses on HTTP URIs, since they're arguably the most common. If you have a specialized scheme you'd like to have supported, let me know.\n\n## Installation \n\n'''\n    npm install valid-url\n'''\n\n## Methods\n'''javascript\n/*\n * @Function isUri(value)\n *\n * @Synopsis  is the value a well-formed uri?\n * @Description  \n        Returns the untainted URI if the test value appears to be well-formed.  Note that\n        you may really want one of the more practical methods like is_http_uri or is_https_uri,\n        since the URI standard (RFC 3986) allows a lot of things you probably don't want.\n * @Arguments \n *   value  The potential URI to test.\n *\n * @Returns The untainted RFC 3986 URI on success, undefined on failure.\n * @Notes \n        This function does not make any attempt to check whether the URI is accessible\n        or 'makes sense' in any meaningful way.  It just checks that it is formatted\n        correctly.\n *\n */\n\n\n/*\n * @Function isHttpUri(value)\n * @Synopsis   is the value a well-formed HTTP uri?\n * @Description  \n        Specialized version of isUri() that only likes http:// urls.  As a result, it can\n        also do a much more thorough job validating.  Also, unlike isUri() it is more\n        concerned with only allowing real-world URIs through.  Things like relative\n        hostnames are allowed by the standards, but probably aren't wise.  Conversely,\n        null paths aren't allowed per RFC 2616 (should be '/' instead), but are allowed\n        by this function.\n        \n        This function only works for fully-qualified URIs.  /bob.html won't work.  \n        See RFC 3986 for the appropriate method to turn a relative URI into an absolute \n        one given its context.\n        \n        Returns the untainted URI if the test value appears to be well-formed.\n        \n        Note that you probably want to either call this in combo with is_https_uri(). i.e.\n        \n        if(isHttpUri(uri) || isHttpsUri(uri)) console.log('Good');\n        \n        or use the convenience method isWebUri which is equivalent.\n\n * @Arguments \n *   value  The potential URI to test.\n *\n * @Returns The untainted RFC 3986 URI on success, undefined on failure.\n * @Notes \n        This function does not make any attempt to check whether the URI is accessible\n        or 'makes sense' in any meaningful way.  It just checks that it is formatted\n        correctly.\n */\n \n\n\n/*\n * @Function isHttpsUri(value)\n * @Synopsis   is the value a well-formed HTTPS uri?\n * @Description  \n        See is_http_uri() for details.  This version only likes the https URI scheme.\n        Otherwise it's identical to is_http_uri()\n * @Arguments \n *   value  The potential URI to test.\n *\n * @Returns The untainted RFC 3986 URI on success, undefined on failure.\n * @Notes \n        This function does not make any attempt to check whether the URI is accessible\n        or 'makes sense' in any meaningful way.  It just checks that it is formatted\n        correctly.\n */\n \n \n /*\n * @Function isWebUri(value)\n * @Synopsis   is the value a well-formed HTTP or HTTPS uri?\n * @Description  \n        This is just a convenience method that combines isHttpUri and isHttpsUri\n        to accept most common real-world URLs.\n * @Arguments \n *   value  The potential URI to test.\n *\n * @Returns The untainted RFC 3986 URI on success, undefined on failure.\n * @Notes \n        This function does not make any attempt to check whether the URI is accessible\n        or 'makes sense' in any meaningful way.  It just checks that it is formatted\n        correctly.\n */\n \n'''\n\n## See also \n\nRFC 3986, RFC 3966, RFC 4694, RFC 4759, RFC 4904\n\n",
    "readmeFilename": "README.md",
    "repository": {
        "url": "git://github.com/ogt/valid-url.git"
    },
    "scripts": {
        "test": "make test"
    },
    "version": "1.0.9"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module valid-url](#apidoc.module.valid-url)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>isHttpUri (value, allowHttps)](#apidoc.element.valid-url.isHttpUri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>isHttpsUri (value)](#apidoc.element.valid-url.isHttpsUri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>isUri (value)](#apidoc.element.valid-url.isUri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>isWebUri (value)](#apidoc.element.valid-url.isWebUri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>is_http_uri (value, allowHttps)](#apidoc.element.valid-url.is_http_uri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>is_https_uri (value)](#apidoc.element.valid-url.is_https_uri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>is_uri (value)](#apidoc.element.valid-url.is_uri)
1.  [function <span class="apidocSignatureSpan">valid-url.</span>is_web_uri (value)](#apidoc.element.valid-url.is_web_uri)



# <a name="apidoc.module.valid-url"></a>[module valid-url](#apidoc.module.valid-url)

#### <a name="apidoc.element.valid-url.isHttpUri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>isHttpUri (value, allowHttps)](#apidoc.element.valid-url.isHttpUri)
- description and source-code
```javascript
function is_http_iri(value, allowHttps) {
    if (!is_iri(value)) {
        return;
    }

    var splitted = [];
    var scheme = '';
    var authority = '';
    var path = '';
    var port = '';
    var query = '';
    var fragment = '';
    var out = '';

    // from RFC 3986
    splitted = splitUri(value);
    scheme = splitted[1];
    authority = splitted[2];
    path = splitted[3];
    query = splitted[4];
    fragment = splitted[5];

    if (!scheme)  return;

    if(allowHttps) {
        if (scheme.toLowerCase() != 'https') return;
    } else {
        if (scheme.toLowerCase() != 'http') return;
    }

    // fully-qualified URIs must have an authority section that is
    // a valid host
    if (!authority) {
        return;
    }

    // enable port component
    if (/:(\d+)$/.test(authority)) {
        port = authority.match(/:(\d+)$/)[0];
        authority = authority.replace(/:\d+$/, '');
    }

    out += scheme + ':';
    out += '//' + authority;

    if (port) {
        out += port;
    }

    out += path;

    if(query && query.length){
        out += '?' + query;
    }

    if(fragment && fragment.length){
        out += '#' + fragment;
    }

    return out;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.isHttpsUri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>isHttpsUri (value)](#apidoc.element.valid-url.isHttpsUri)
- description and source-code
```javascript
function is_https_iri(value) {
    return is_http_iri(value, true);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.isUri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>isUri (value)](#apidoc.element.valid-url.isUri)
- description and source-code
```javascript
function is_iri(value) {
    if (!value) {
        return;
    }

    // check for illegal characters
    if (/[^a-z0-9\:\/\?\#\[\]\@\!\$\&\'\(\)\*\+\,\;\=\.\-\_\~\%]/i.test(value)) return;

    // check for hex escapes that aren't complete
    if (/%[^0-9a-f]/i.test(value)) return;
    if (/%[0-9a-f](:?[^0-9a-f]|$)/i.test(value)) return;

    var splitted = [];
    var scheme = '';
    var authority = '';
    var path = '';
    var query = '';
    var fragment = '';
    var out = '';

    // from RFC 3986
    splitted = splitUri(value);
    scheme = splitted[1];
    authority = splitted[2];
    path = splitted[3];
    query = splitted[4];
    fragment = splitted[5];

    // scheme and path are required, though the path can be empty
    if (!(scheme && scheme.length && path.length >= 0)) return;

    // if authority is present, the path must be empty or begin with a /
    if (authority && authority.length) {
        if (!(path.length === 0 || /^\//.test(path))) return;
    } else {
        // if authority is not present, the path must not start with //
        if (/^\/\//.test(path)) return;
    }

    // scheme must begin with a letter, then consist of letters, digits, +, ., or -
    if (!/^[a-z][a-z0-9\+\-\.]*$/.test(scheme.toLowerCase()))  return;

    // re-assemble the URL per section 5.3 in RFC 3986
    out += scheme + ':';
    if (authority && authority.length) {
        out += '//' + authority;
    }

    out += path;

    if (query && query.length) {
        out += '?' + query;
    }

    if (fragment && fragment.length) {
        out += '#' + fragment;
    }

    return out;
}
```
- example usage
```shell
...

## Synopsis

Common url validation methods
'''
    var validUrl = require('valid-url');

    if (validUrl.isUri(suspect)){
        console.log('Looks like an URI');
    } else {
        console.log('Not a URI');
    }
'''

Replicates the functionality of Richard Sonnen <sonnen@richardsonnen.com> perl module :
...
```

#### <a name="apidoc.element.valid-url.isWebUri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>isWebUri (value)](#apidoc.element.valid-url.isWebUri)
- description and source-code
```javascript
function is_web_iri(value) {
    return (is_http_iri(value) || is_https_iri(value));
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.is_http_uri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>is_http_uri (value, allowHttps)](#apidoc.element.valid-url.is_http_uri)
- description and source-code
```javascript
function is_http_iri(value, allowHttps) {
    if (!is_iri(value)) {
        return;
    }

    var splitted = [];
    var scheme = '';
    var authority = '';
    var path = '';
    var port = '';
    var query = '';
    var fragment = '';
    var out = '';

    // from RFC 3986
    splitted = splitUri(value);
    scheme = splitted[1];
    authority = splitted[2];
    path = splitted[3];
    query = splitted[4];
    fragment = splitted[5];

    if (!scheme)  return;

    if(allowHttps) {
        if (scheme.toLowerCase() != 'https') return;
    } else {
        if (scheme.toLowerCase() != 'http') return;
    }

    // fully-qualified URIs must have an authority section that is
    // a valid host
    if (!authority) {
        return;
    }

    // enable port component
    if (/:(\d+)$/.test(authority)) {
        port = authority.match(/:(\d+)$/)[0];
        authority = authority.replace(/:\d+$/, '');
    }

    out += scheme + ':';
    out += '//' + authority;

    if (port) {
        out += port;
    }

    out += path;

    if(query && query.length){
        out += '?' + query;
    }

    if(fragment && fragment.length){
        out += '#' + fragment;
    }

    return out;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.is_https_uri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>is_https_uri (value)](#apidoc.element.valid-url.is_https_uri)
- description and source-code
```javascript
function is_https_iri(value) {
    return is_http_iri(value, true);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.is_uri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>is_uri (value)](#apidoc.element.valid-url.is_uri)
- description and source-code
```javascript
function is_iri(value) {
    if (!value) {
        return;
    }

    // check for illegal characters
    if (/[^a-z0-9\:\/\?\#\[\]\@\!\$\&\'\(\)\*\+\,\;\=\.\-\_\~\%]/i.test(value)) return;

    // check for hex escapes that aren't complete
    if (/%[^0-9a-f]/i.test(value)) return;
    if (/%[0-9a-f](:?[^0-9a-f]|$)/i.test(value)) return;

    var splitted = [];
    var scheme = '';
    var authority = '';
    var path = '';
    var query = '';
    var fragment = '';
    var out = '';

    // from RFC 3986
    splitted = splitUri(value);
    scheme = splitted[1];
    authority = splitted[2];
    path = splitted[3];
    query = splitted[4];
    fragment = splitted[5];

    // scheme and path are required, though the path can be empty
    if (!(scheme && scheme.length && path.length >= 0)) return;

    // if authority is present, the path must be empty or begin with a /
    if (authority && authority.length) {
        if (!(path.length === 0 || /^\//.test(path))) return;
    } else {
        // if authority is not present, the path must not start with //
        if (/^\/\//.test(path)) return;
    }

    // scheme must begin with a letter, then consist of letters, digits, +, ., or -
    if (!/^[a-z][a-z0-9\+\-\.]*$/.test(scheme.toLowerCase()))  return;

    // re-assemble the URL per section 5.3 in RFC 3986
    out += scheme + ':';
    if (authority && authority.length) {
        out += '//' + authority;
    }

    out += path;

    if (query && query.length) {
        out += '?' + query;
    }

    if (fragment && fragment.length) {
        out += '#' + fragment;
    }

    return out;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.valid-url.is_web_uri"></a>[function <span class="apidocSignatureSpan">valid-url.</span>is_web_uri (value)](#apidoc.element.valid-url.is_web_uri)
- description and source-code
```javascript
function is_web_iri(value) {
    return (is_http_iri(value) || is_https_iri(value));
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
