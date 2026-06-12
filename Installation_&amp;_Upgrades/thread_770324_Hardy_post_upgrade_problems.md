---
title: "Hardy post upgrade problems"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by rstuart on 2008-04-27
Hi All,

Have been using ubuntu for over a year now and very happy with it. I usually try to back up my home directory and whatever else i need before formatting my HD and installing the new ubuntu version but this time i decided to try out the upgrade.

Everything went fine for the most part, however, there is a small problem. After the upgrade, logging in doesn't go as smoothly as it used to. When i boot up, the login GUI (GDM i believe) is displayed, all is good and well. When i login for the first time, a blank screen is displayed for a little while before eventually logging me out (i can tell becuase it displays the usual lines in a console when you usually log out like "Running rc.local"). It then presents me with a GDM login screen again. This time, when i log in, all goes well.

I wasn't sure what on earth the problem could be. I booted in recovery mode and regenerated my xorg.conf before trying agian but same problem. I then when looking at the xorg logs and came up with the following two files.....

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux rstuart-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 20:58:46 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01d8 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 1028,01d8 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1028,01d8 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01d8 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01d8 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01d8 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01d8 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01d8 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01d8 rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,170c card 1028,01d8 rev 02 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 1180,0832 card 1028,01d8 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:01:1: chip 1180,0822 card 1028,01d8 rev 19 class 08,05,01 hdr 80
(II) PCI: 02:01:2: chip 1180,0592 card 1028,01d8 rev 0a class 08,80,00 hdr 80
(II) PCI: 02:01:3: chip 1180,0852 card 1028,01d8 rev 05 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1022 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfcfffff (0x300000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdf9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdff00000/19, 0xc0000000/28, 0xdfec0000/18, I/O @ 0xeff8/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdff80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[5] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[5] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Generic Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1440x900
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00020000 to 0x00020203
(WW) intel(0): PIPEASTAT before: status: VBLANK_INT_ENABLE
(WW) intel(0): PIPEASTAT after: status: VBLANK_INT_ENABLE VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[8] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[9] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[10] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[11] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[12] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[13] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[14] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[15] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[16] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000eff8 - 0x0000efff (0x8) IS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[26] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[32] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[33] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[34] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[35] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): [drm] Registers = 0xdff00000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): [drm] mapped back buffer at 0xc5000000, handle = 0xc5000000
(II) intel(0): [drm] mapped depth buffer at 0xc6000000, handle = 0xc6000000
(II) intel(0): [drm] mapped classic textures at 0xc7000000, handle = 0xc7000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 35389440 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x06000000 (pgoffset 24576)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x07000000 (pgoffset 28672)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (11520 kB) X tiled
(II) intel(0): 0x02000000-0x041bffff: exa offscreen (34560 kB)
(II) intel(0): 0x05000000-0x05ffffff: back buffer (11520 kB) X tiled
(II) intel(0): 0x06000000-0x06ffffff: depth buffer (11520 kB) X tiled
(II) intel(0): 0x07000000-0x08ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 303 x 190
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): fbc disabled on plane a
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4

```

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux rstuart-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 27 20:55:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01d8 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 1028,01d8 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1028,01d8 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01d8 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01d8 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01d8 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01d8 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01d8 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01d8 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01d8 rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,170c card 1028,01d8 rev 02 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 1180,0832 card 1028,01d8 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:01:1: chip 1180,0822 card 1028,01d8 rev 19 class 08,05,01 hdr 80
(II) PCI: 02:01:2: chip 1180,0592 card 1028,01d8 rev 0a class 08,80,00 hdr 80
(II) PCI: 02:01:3: chip 1180,0852 card 1028,01d8 rev 05 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1022 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfcfffff (0x300000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdf9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdff00000/19, 0xc0000000/28, 0xdfec0000/18, I/O @ 0xeff8/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdff80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[5] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[1] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[2] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[3] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[4] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[5] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[9] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[10] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[11] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[12] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[13] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Generic Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1440x900
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00020000 to 0x80020203
(WW) intel(0): PIPEASTAT before: status: VBLANK_INT_ENABLE
(WW) intel(0): PIPEASTAT after: status: FIFO_UNDERRUN VBLANK_INT_ENABLE VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfdff000 - 0xdfdfffff (0x1000) MX[B]
	[8] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[9] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[10] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[11] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[12] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[13] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[14] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[15] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[16] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000eff8 - 0x0000efff (0x8) IS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[26] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[32] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[33] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[34] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[35] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): [drm] Registers = 0xdff00000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): [drm] mapped back buffer at 0xc5000000, handle = 0xc5000000
(II) intel(0): [drm] mapped depth buffer at 0xc6000000, handle = 0xc6000000
(II) intel(0): [drm] mapped classic textures at 0xc7000000, handle = 0xc7000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 35389440 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x06000000 (pgoffset 24576)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x07000000 (pgoffset 28672)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (11520 kB) X tiled
(II) intel(0): 0x02000000-0x041bffff: exa offscreen (34560 kB)
(II) intel(0): 0x05000000-0x05ffffff: back buffer (11520 kB) X tiled
(II) intel(0): 0x06000000-0x06ffffff: depth buffer (11520 kB) X tiled
(II) intel(0): 0x07000000-0x08ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 303 x 190
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): fbc disabled on plane a
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x06000000 (pgoffset 24576)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x07000000 (pgoffset 28672)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (11520 kB) X tiled
(II) intel(0): 0x02000000-0x041bffff: exa offscreen (34560 kB)
(II) intel(0): 0x05000000-0x05ffffff: back buffer (11520 kB) X tiled
(II) intel(0): 0x06000000-0x06ffffff: depth buffer (11520 kB) X tiled
(II) intel(0): 0x07000000-0x08ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0x28200000
(II) intel(0): [drm] dma control initialized, using IRQ 16
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
SetClientVersion: 0 9
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "SEC", prod id 17495
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f4c420]
2: /usr/lib/xorg/modules//libfb.so(fbOddTile+0x118) [0xb79dcb98]
3: /usr/lib/xorg/modules//libfb.so(fbTile+0x8c) [0xb79dcc5c]
4: /usr/lib/xorg/modules//libfb.so(fbFillRegionTiled+0x19e) [0xb79dd2ee]
5: /usr/lib/xorg/modules//libfb.so(fbPaintWindow+0x104) [0xb79dd5a4]
6: /usr/lib/xorg/modules//libexa.so(ExaCheckPaintWindow+0x40) [0xb79bf9e0]
7: /usr/lib/xorg/modules//libexa.so(exaPaintWindow+0xb4) [0xb79b9e54]
8: /usr/lib/xorg/modules//libfb.so(fbPaintWindow+0xb9) [0xb79dd559]
9: /usr/lib/xorg/modules//libexa.so(ExaCheckPaintWindow+0x40) [0xb79bf9e0]
10: /usr/lib/xorg/modules//libexa.so(exaPaintWindow+0xb4) [0xb79b9e54]
11: /usr/bin/X [0x817083f]
12: /usr/bin/X(compPaintWindowBackground+0x6d) [0x810530d]
13: /usr/bin/X(miWindowExposures+0xf2) [0x8121282]
14: /usr/lib/xorg/modules/extensions//libdri.so(DRIWindowExposures+0x8d) [0xb7b4acdd]
15: /usr/bin/X [0x80db995]
16: /usr/bin/X(miHandleValidateExposures+0x78) [0x81373b8]
17: /usr/bin/X [0x80d35d6]
18: /usr/bin/X(xf86EnableDisableFBAccess+0x91) [0x80d3751]
19: /usr/lib/xorg/modules//libexa.so [0xb79b7040]
20: /usr/bin/X [0x80fcbd3]
21: /usr/bin/X(xf86Wakeup+0x21c) [0x80c831c]
22: /usr/bin/X(WakeupHandler+0x59) [0x8091719]
23: /usr/bin/X(WaitForSomething+0x1e2) [0x81b1d22]
24: /usr/bin/X(Dispatch+0x8d) [0x808d69d]
25: /usr/bin/X(main+0x48b) [0x807471b]
26: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ce1450]
27: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): fbc disabled on plane a
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4

```

From what i can tell, the first (Xorg.o.log) is the log file from a successful login, the second (Xorg.0.log.old) is what produced when it logs me out the first time. You'll notice the second has a pretty lengthy error at the end. I'm a relitave xorg beginner, but it doesn't look good. Can anyone tell me what might be my next step in resolving this problem? Although its not a show stopping problem for me, having to log in twice is a bit of a pain.

My xorg.conf is below. I have a Dell 640m laptop with a 1440x900 resolution (I have the 915resolution package installed and also the xserver-xorg-video-intel package, i might try removing 915resolution first).

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Thanks

---

### Post by rstuart on 2008-04-27
No one can help me?

---

### Post by ghstridr on 2008-04-27
Well, the traceback portion of the log file looks like it's having framebuffer (fb) issues.  I would try removing all the chipset specific drivers first and only try the standard vesa drivers at 1024x768 for a bit.  
If, say after 3-7 days, everything is good, try the intel drivers with out any addons.  Make sure you correctly specify your lcd screen.  You will probably have to do some searching around and setup some mode lines in your xorg.conf for your screen.

The reason I say 3-7 days is to shake out any possible bugs in either the base software or the hardware.  The vesa driver works with nearly everything, it just doesn't provide any acceleration or frills.  That makes it a good testing tool.

---

### Post by rstuart on 2008-04-28
Thanks for the help. I ended up formatting my machine and installing a fresh copy of Hardy before restoring the software i like to use and i had the same problem. I just stopped my system monitor conky being started when gnome starts (via the sessions dialog), it fixed the problem. 

Seems like it is a conky problem, not ubuntu.

For reference, my conkyrc is below. Anyone else have this problem with conky?

```

# conky configuration
# edited by ryan+conky@stuart.id.au 

background yes
use_xft yes
xftfont Terminus:size=8
out_to_console no
update_interval 2.0
total_run_times 0
own_window no
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_right
maximum_width 270
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
gap_y 1
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer yes

TEXT

${color #ddaa00}${time %a, } ${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}BATTERY: ${color }$battery
${color slate grey}CPU:${color } $cpu%  ${acpitemp}C
${cpugraph 20,130 ddaa00 ddaa00}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top cpu 1}%
${color lightgrey} ${top name 2}$alignr${top cpu 2}%
${color lightgrey} ${top name 3}$alignr${top cpu 3}%
${color lightgrey} ${top name 4}$alignr${top cpu 4}%

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}%
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}%
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}%
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}%

${color slate grey}MEM: ${color }$memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}DISK: ${color }$diskio
${diskiograph 20,130 ddaa00 ddaa00}

${color slate grey}WIRELESS: ${color }${wireless_essid wlan0}$alignr${color #ddaa00}${wireless_link_qual wlan0}%
${color}Up:$alignr${color }${upspeed wlan0} k/s
${upspeedgraph eth0 20,130 ddaa00 ddaa00}
${color}Down:$alignr${color }${downspeed wlan0}k/s${color}
${downspeedgraph wlan0 20,130 ddaa00 ddaa00}

```

---

