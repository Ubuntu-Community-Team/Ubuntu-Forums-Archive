---
title: "Building drivers from rpm but getting stuck!  Help please :)"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by DaveAK on 2007-07-20
I'm building drivers for my 3M TouchScreen. Can someone take a look and see if this will work for Feisty?

[http://solutions.3m.com/wps/portal/3.../TouchDrivers/](http://solutions.3m.com/wps/portal/3.../TouchDrivers/)

I get so far and after issuing 'rpmbuild -ba TWDrv.spec' get this as the first of many errors :

/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:12:35: error: linux/devfs_fs_kernel.h: No such file or directory

What do I need to do next?

---

