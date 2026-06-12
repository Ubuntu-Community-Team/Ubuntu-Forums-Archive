---
title: "Fix-broken error"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by GabrielWolff on 2005-11-11
Hey!

While trying to fix a broken package, I got the following error message. Should it bother me?

E: /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb: trying to overwrite `/usr/lib/openoffice2/help/en/scalc.idx/DOCS.TAB', which is also in package openoffice.org2-calc

EDIT: I guess it should - since then every installation stops with the same error message, even if it's got nothing to do with openoffice

Thanx

---

### Post by Xian on 2005-11-11
Remove the package below before installing anything else.
Then do your upgrade/installation.

Afterwards, you should be able to reinstall it on your system.

```
$ sudo apt-get remove openoffice.org2-help-en-us
```

---

