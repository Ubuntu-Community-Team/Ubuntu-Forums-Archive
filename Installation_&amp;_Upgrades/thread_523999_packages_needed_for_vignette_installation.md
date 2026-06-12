---
title: "packages needed for vignette installation"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by dahagama on 2007-08-12
I need following packages for Vignette Installation. Can you please let me know  how to get them and if they already come with Ubuntu by default?

compat-libstdc++-devel
compat-gcc-*
compat-libstdc++*
libXp*

---

### Post by dfreer on 2007-08-12
please don't post the same question in multiple forums...
[http://ubuntuforums.org/showthread.php?t=523999](http://ubuntuforums.org/showthread.php?t=523999)
As for those packages, I think these are the packages you need:

libstdc++2.10-dev
build-essential
libstdc++5
libxp6

You should be able to install all of those from the standard repositories, with a regular:
```
sudo apt-get install
```

EDIT: I don't use vignette, so I do not know if this is everything you need to install it, or even if it is installable.

---

