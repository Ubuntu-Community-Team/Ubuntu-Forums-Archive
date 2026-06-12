---
title: "Lucid and iPhone"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-02-10
Hi All,

Any chances of iPhone sync working in Lucid. I am following this tutorial.

[http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html)

I am getting the following error.

> sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs is already the newest version.
gvfs-backends is already the newest version.
gvfs-bin is already the newest version.
gvfs-fuse is already the newest version.
libgvfscommon0 is already the newest version.
libgpod-common is already the newest version.
Package libiphone-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libimobiledevice-utils
E: Package libiphone-utils has no installation candidate


Thanks.
SK

---

### Post by alexmurray on 2010-02-11
You don't need libiphone-utils so remove it from the list of packages to be installed.

---

