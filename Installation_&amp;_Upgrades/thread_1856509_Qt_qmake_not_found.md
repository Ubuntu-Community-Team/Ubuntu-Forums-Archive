---
title: "Qt qmake not found"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by Virtual_Ron on 2011-10-08
Hi Guys,

Been trying to compile the ktorrent source (4.1.*) for the past few releases, but keep getting snagged with the following error:

> ronb@vulcan:~/Programs/ktorrent-4.1.2/build$ **cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..**
CMake Error at /usr/share/cmake-2.8/Modules/FindQt4.cmake:1148 (MESSAGE):
**  Qt qmake not found!**
Call Stack (most recent call first):
  CMakeLists.txt:2 (find_package)
-- Configuring incomplete, errors occurred!

I'm not sure how to get past this. qmake IS installed (/usr/bin/qmake).

ideas?
Thanks!
Ron

PS: running kubuntu 11.04 x64 (2.6.38-11-generic)

---

