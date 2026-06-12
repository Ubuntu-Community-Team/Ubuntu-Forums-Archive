---
title: "Installer starts, then can't find cd-rom"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by wlk on 2010-01-09
Hopefully this will help someone.  I was having trouble trying to install either ubuntu 9.10 and opensuse 11.2 (each a fresh install on the box).  On both, the installer would start, but during the install process it would no be able to find/mount the cd-rom (DVD, in this case), and so it could go no further.  I had no problems on this box with live cds, some other distros, and had previously installed opensuse 11.0 with no problem.  Eventually, I discovered that I had the jumpers on the DVD drive set to "slave".  When I switched them to "master", I was able to proceed with both installs.

---

