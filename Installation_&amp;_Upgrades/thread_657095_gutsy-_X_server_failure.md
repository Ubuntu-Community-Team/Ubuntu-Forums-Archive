---
title: "gutsy- X server failure?"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by ktindle on 2008-01-03
After a fresh install of gutsy desktop, alt AMD64, grub boots, normal splash screen with progress bar all the way to the end, then hangs on a text mode screen with "running local boot scripts".

This is a Gigabyte GA-M61SME-S2 with 2G, AMD 64 X2 5600+, and I am using the integrated GeForce 6100 video.

It seems the X server is not starting.

---

### Post by ktindle on 2008-01-04
The X server was not starting, because the GeForce could not be detected, and so was unconfigured.  A boot in recovery mode with a manual X configuration via dpkg-reconfigure, and things seem OK.

---

