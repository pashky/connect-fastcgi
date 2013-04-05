# What

connect middleware to pass requests to FastCGI server process.

# Why

Because PHP-FPM. Yes, that's right, it's insanity, but I need it, mainly
for development and automated testing tasks I do with grunt and simple
node.js scripts.

This module is a stripped down version of this
https://github.com/davidcoallier/node-php server converted to connect
middleware. It was then modified to support POST and PUT, pass
required headers etc.

# How

```javascript
var connect = require('connect'), 
    php = require('../connect-fastcgi');

var app = connect()
        .use('/php', php({ fastcgiPort: 8002, fastcgiHost: 'localhost', root: "./php" }))
        .use(connect.logger())
        .use(connect.static('./assets'))
        .listen(3000);
```

Available options:

- `root:` root directory for scripts
- `fastcgiHost:` host or socket path to FastCGI process
- `fastcgiPort:` port

# Thanks

[David Coallier](https://github.com/davidcoallier) for original node-php module

