---
title: "Fixing up a haskell problem (possibly WashNGo or regex related)"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by ralphmerridew on 2008-05-01
My install has somehow gotten a bit messed-up:

Any usage of apt-get (including trying to uninstall the offending package) gives the additional output:

Setting up libghc6-wash-dev (2.12-5) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/WashNGo-2.12/installed-pkg-config" ... done.
ghc-pkg: dependency regex-compat-0.91 doesn't exist (use --force to override)
dpkg: error processing libghc6-wash-dev (--configure):
 subprocess post-installation script returned error exit status 1
...
Errors were encountered while processing:
 libghc6-wash-dev

While I can install & uninstall other stuff, it would be nice to stop that complaining.

Haskell is not important on my system, so removing it is okay.

---

### Post by ralphmerridew on 2008-05-01
Managed to get rid of it by editing /usr/lib/haskell-packages/ghc6/lib/WashNGo-2.12/installed-pkg-config to remove regex-compat & some other dependency; that tricked it into thinking it was fully installed so it could be removed.

---

