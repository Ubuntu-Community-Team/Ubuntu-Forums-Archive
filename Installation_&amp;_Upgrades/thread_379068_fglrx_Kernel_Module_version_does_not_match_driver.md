---
title: "fglrx: Kernel Module version does *not* match driver"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Dj_Extreme_Audiophile on 2007-03-08
Hey guys, I'm trying to get 3D acceleration to work on my x700, 

I'm getting this in my xorg.0.log :
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.33.6
(II) fglrx(0):     Date: Jan  8 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7988000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Will installing a previous ATI driver work for this?

---

### Post by pay on 2007-03-08
What kernel do you have? uname -r

---

### Post by Dj_Extreme_Audiophile on 2007-03-08
> **pay said:**
> What kernel do you have? uname -r

john@johnmcd-engg:~$ uname -r
2.6.17-11-generic

---

