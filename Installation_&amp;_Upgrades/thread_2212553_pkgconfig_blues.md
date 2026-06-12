---
title: "pkgconfig blues"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by nibal on 2014-03-21
This is rather an improvement suggestion. Out of the 1000s of Ubuntu packages I have installed, only 21 have .pc (pkconfig file) files. This might not be a problem if you only use ubuntu's packages, but the minute you start compiling from sources you get into trouble.

I realize that when sources do not build such files, it is difficult to do anything about it. However, when building a package from sources, one knows the CFLAGS he uses, the -l extension, if it is a library, installation paths and everything else that goes into a .pc file. After all pkgconfig has to do with packages and packaging.

So, please, Ubuntu package maintainers make a more concerted effort of providing the .pc files required by most source software. If not, developers may be forced to change distro, and ubuntu will become another desktop environment, short in substance and big in looks :-(

---

### Post by nibal on 2014-03-21
> So, please, Ubuntu package maintainers make a more concerted effort of providing the .pc files required by most source software. If not, developers may be forced to change distro, and ubuntu will become another desktop environment, short in substance and big in looks :-(

Actually, .pc files are only associated with dev packages. So I may only have 21 dev packages in my distro. Please scratch my previous comment, unless proven otherwise.

---

### Post by steeldriver on 2014-03-21
... even -dev packages shouldn't really need to provide .pc files unless they put their header files / libraries somewhere that's not on the standard search paths, I think

---

