---
title: "Upgrade Intel Driver from 01.org for Mythbuntu 12.04.3"
date: 2013-10-03
forum: Installation &amp; Upgrades
---

### Post by ODBWilson on 2013-10-03
I try to follow the build guide from [https://01.org/linuxgraphics/documentation/build-guide](https://01.org/linuxgraphics/documentation/build-guide).
And install the following packages from scratch.

 
[LIST]
[*][xf86-video-intel - 2.99.902]("http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.99.902.tar.gz")
[*][Libdrm - 2.4.46]("http://dri.freedesktop.org/libdrm/libdrm-2.4.46.tar.gz")
[*][Libva - 1.2.1]("http://www.freedesktop.org/software/vaapi/releases/libva/libva-1.2.1.tar.bz2")
[*][vaapi intel-driver - 1.2.1]("http://www.freedesktop.org/software/vaapi/releases/libva-intel-driver/libva-intel-driver-1.2.1.tar.bz2")
[*][Xserver Xorg - 1.14.2]("http://ftp.x.org/pub/individual/xserver/xorg-server-1.14.2.tar.bz2")
[/LIST]
 

After the installation, the systems reports errors as below:
[I][B]
X.Org X Server 1.13.3[/B][/I]   ***(old release)***
	Release Date: 2013-03-07
	[     4.891] X Protocol Version 11, Revision 0

 ........
 .......
 [ 93440.560] (EE) Backtrace:
	[ 93440.562] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb7693e29]
	[ 93440.562] (EE) 1: /usr/bin/X (0xb74dc000+0x1bbc2a) [0xb7697c2a]
	[ 93440.562] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb74b940c]
	[ 93440.562] (EE) 3: /usr/bin/X (0xb74dc000+0xcd762) [0xb75a9762]
	[ 93440.562] (EE) 4: /usr/bin/X (0xb74dc000+0x1a0bc8) [0xb767cbc8]
	[ 93440.562] (EE) 5: /usr/bin/X (0xb74dc000+0x12f1a2) [0xb760b1a2]
	[ 93440.562] (EE) 6: /usr/bin/X (FreeCursor+0x54) [0xb750b6e4]
	[ 93440.562] (EE) 7: /usr/bin/X (0xb74dc000+0x56547) [0xb7532547]
	[ 93440.562] (EE) 8: /usr/bin/X (0xb74dc000+0x303d3) [0xb750c3d3]
	[ 93440.563] (EE) 9: /usr/bin/X (0xb74dc000+0x30b80) [0xb750cb80]
	[ 93440.563] (EE) 10: /usr/bin/X (0xb74dc000+0x29a17) [0xb7505a17]
	[ 93440.563] (EE) 11: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb71344d3]
	[ 93440.563] (EE) 12: /usr/bin/X (0xb74dc000+0x29d69) [0xb7505d69]
	[ 93440.563] (EE)
	[ 93440.563] (EE) Segmentation fault at address 0x0
	[ 93440.563]
	Fatal server error:
	[ 93440.563] Caught signal 11 (Segmentation fault). Server aborting
	[ 93440.563]
	[ 93440.563] (EE)
	 
 Actually, the system is still using the old xorg, and it didn't use the newly compiled xorg under /usr/local/bin/

From the build guide
==============
If you install xorg in another directory (referred to as $XORG_DIR),  instead of overriding the xorg shipped in your Linux distribution, you  need to set two macros at first: $ export  PKG_CONFIG_PATH=${XORG_DIR}/lib/pkgconfig:$PKG_CONFIG_PATH $ export  ACLOCAL="aclocal -I ${XORG_DIR}/share/aclocal".

What is the XORG_DIR for Mythbuntu 12.04.3?
Does anyone successfully install the Intel driver manually from 01.org?  And how?

Cheers,
Wilson

---

