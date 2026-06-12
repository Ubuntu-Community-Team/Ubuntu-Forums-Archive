---
title: "Broken Index"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by grathinam on 2010-07-06
Hi

When I try to upgrade /update any of the software component it is complaining stating that "Broken Repository Index" I did search on this forum and tried the following command but that did not work either.

any ideas how to resolve this 

grathinam@ubuntu07:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on x11-apps; however:
  Package x11-apps is not installed.
 xbase-clients depends on x11-session-utils; however:
  Package x11-session-utils is not installed.
 xbase-clients depends on x11-utils; however:
  Package x11-utils is not installed.
 xbase-clients depends on x11-xfs-utils; however:
  Package x11-xfs-utils is not installed.
 xbase-clients depends on x11-xkb-utils; however:
  Package x11-xkb-utils is not installed.
 xbase-clients depends on x11-xserver-utils; however:
  Package x11-xserver-utils is not installed.
dpkg: error processing xbase-clients (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.7-10ubuntu6); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xbase-clients
 libc6-dev

---

