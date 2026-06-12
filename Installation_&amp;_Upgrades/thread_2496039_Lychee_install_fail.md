---
title: "Lychee install fail"
date: 2024-03-12
forum: Installation &amp; Upgrades
---

### Post by bsfoto on 2024-03-12
Hello,

I want reinstall the Lychee gallery, with git and composer, but i cant continue because i get this messege:

node:internal/modules/cjs/loader:1142
  const err = new Error(message);
              ^


Error: Cannot find module 'semver'
Require stack:
- /usr/share/nodejs/npm/lib/utils/unsupported.js
- /usr/share/nodejs/npm/lib/cli.js
- /usr/share/nodejs/npm/bin/npm-cli.js
    at Module._resolveFilename (node:internal/modules/cjs/loader:1142:15)
    at Module._load (node:internal/modules/cjs/loader:983:27)
    at Module.require (node:internal/modules/cjs/loader:1230:19)
    at require (node:internal/modules/helpers:179:18)
    at Object.<anonymous> (/usr/share/nodejs/npm/lib/utils/unsupported.js:2:16)
    at Module._compile (node:internal/modules/cjs/loader:1368:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1426:10)
    at Module.load (node:internal/modules/cjs/loader:1205:32)
    at Module._load (node:internal/modules/cjs/loader:1021:12)
    at Module.require (node:internal/modules/cjs/loader:1230:19) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [
    '/usr/share/nodejs/npm/lib/utils/unsupported.js',
    '/usr/share/nodejs/npm/lib/cli.js',
    '/usr/share/nodejs/npm/bin/npm-cli.js'
  ]
}


Node.js v21.7.1

can sombody help me? i tried find more information from google, but im beginner.

thxxx.

---

