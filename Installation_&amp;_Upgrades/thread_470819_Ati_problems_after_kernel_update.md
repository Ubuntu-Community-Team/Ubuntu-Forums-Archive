---
title: "Ati problems after kernel update"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by carpex on 2007-06-11
Hi, I did an update this morning, I believe from kernel 2.6.20-16.28 to 2.6.20-16.29. After rebooting, I couldn't get into an xgl session. Before this upgrade, I had ati drivers (8.37.6-x86.x86_64 installed from their website) + xgl +beryl working fine. Now, it seems to revert to mesa drivers. If I type fglrxinfo, I get mesa  instead of fglrx. My xorg.conf file has stayed untouched and is fine. Here is, I think, the relevant part of my Xorg.0.log file: 

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x4000 at 0x2b02a7b27000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Where is it getting fglrx 8.34.8 from ? I tried reinstalling the proprietary drivers, to no avail. My graphics card is an ATI x1400 and I am running Feisty x86_64.

Any help is appreciated. Thanks

CP

---

### Post by fsando on 2007-06-11
Hi carpex
I have made a description here that might help:

[http://ubuntuforums.org/showthread.php?t=462410](http://ubuntuforums.org/showthread.php?t=462410)

I haven't tested it with the latest (2.6.20-16.29) upgrade but it has worked well with the previous upgrades.

---

### Post by carpex on 2007-06-11
That did not work with the 8.37.6 drivers. It keeps going back to mesa. I had to revert back to the drivers in the repos ;-) ... but now it works ok. 

Thanks, 

Guillaume

---

