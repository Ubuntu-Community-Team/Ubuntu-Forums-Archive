---
title: "unable to make backup link of `./etc/X11/xkb/compiled'"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by kevinbeard on 2006-06-06
I finally got my upgrade finished apart from one thing...

I nede to upgrade xkbutils but everytime I try I get the following error message:

Preparing to replace xkbutils 7.0-3 (using .../xkbutils_1%3a1.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement xkbutils ...
dpkg: error processing /var/cache/apt/archives/xkbutils_1%3a1.0.1-0ubuntu1_i386.deb (--unpack):
 unable to make backup link of `./etc/X11/xkb/compiled' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/xkbutils_1%3a1.0.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Has anyone else come across this?  I have tried removing this file but even as root I get "Operation not permitted"

---

