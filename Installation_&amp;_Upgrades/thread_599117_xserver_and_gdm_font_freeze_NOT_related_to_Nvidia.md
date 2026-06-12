---
title: "xserver and gdm font freeze NOT related to Nvidia"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ivanmladek on 2007-11-01
I have a running nvidia driver for my Nvidia GeForce 7200 and all worked until yesterday when I messed with an Mplayer installation and managed to screw up my font configuration. The Xserver loads up but gets stuck at the gdm login screen. 

Here's the /Xorg.0.log
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ivanmladek-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  1 00:15:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation GeForce Go 7200"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f7 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 103c,30b7 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 103c,30b7 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 103c,30b7 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 103c,30b7 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 103c,30b7 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 103c,30b7 rev f1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 103c,30b7 rev f1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 103c,30b7 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 103c,30b7 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 14e4,4312 card 103c,1360 rev 01 class 02,80,00 hdr 00
(II) PCI: 05:00:0: chip 10de,01d6 card 103c,30b7 rev a1 class 03,00,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30b7 rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30b7 rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0843 card 103c,30b7 rev 01 class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0592 card 103c,30b7 rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:4: chip 1180,0852 card 103c,30b7 rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc03fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc3200000 - 0xc33fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xc0400000 - 0xc05fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:4:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xc1000000 - 0xc2ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:16:0), (0,7,7), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xc3000000 - 0xc30fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xc0040000/18
(--) PCI:*(5:0:0) nVidia Corporation GeForce Go 7200 rev 161, Mem @ 0xc2000000/24, 0xd0000000/28, 0xc1000000/24
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
	[0] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[1] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[2] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[3] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[4] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[5] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[6] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[15] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[18] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[19] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[20] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[1] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[2] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[3] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[4] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[5] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[6] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[8] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[9] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[10] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[11] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[15] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[18] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[19] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[20] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
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
	[4] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[5] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[6] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[7] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[8] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[9] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[10] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[14] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[24] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[25] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[26] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[5] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[6] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[7] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[8] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[9] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[10] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[14] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[24] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[25] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[26] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[5] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[6] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[7] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[8] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[9] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[10] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[12] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[13] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[14] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[15] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[25] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[26] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[27] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[28] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[29] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[30] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7200 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.41.90
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7200 at PCI:5:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xc3001400 - 0xc30014ff (0x100) MX[B]
	[8] -1	0	0xc3001000 - 0xc30010ff (0x100) MX[B]
	[9] -1	0	0xc3000c00 - 0xc3000cff (0x100) MX[B]
	[10] -1	0	0xc3000800 - 0xc30008ff (0x100) MX[B]
	[11] -1	0	0xc3000000 - 0xc30007ff (0x800) MX[B]
	[12] -1	0	0xc0400000 - 0xc0403fff (0x4000) MX[B]
	[13] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[14] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[15] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[16] -1	0	0xc0005000 - 0xc00050ff (0x100) MX[B]
	[17] -1	0	0xc0004000 - 0xc0004fff (0x1000) MX[B]
	[18] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xc2000000 - 0xc2ffffff (0x1000000) MX[B](B)
	[21] -1	0	0xc0040000 - 0xc007ffff (0x40000) MX[B]
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[28] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[29] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[30] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[31] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[32] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[33] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[34] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[35] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[36] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Synaptics DeviceOff called  
```

I have played around with the wacom drivers and they are not the problem. The fonts are not loading up and I have tried everything:
```
apt-get install --reinstall xfonts-base
sudo apt-get install --reinstall gdm
dpkg-reconfigure xserver-xorg
dpkg-reconfigure gdm

```

and nothing, nothing, nothing. 

I have tweaked with the fonts in xorg.conf again to no avail. The problem seems not to be with nvidia drivers or anything which run start smooth according to the previous log. 

and the xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"nVidia Corporation GeForce Go 7200"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce Go 7200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection 
```


```
xinit
```
from safemode loads a window and programs run but again this too little. 

Can anyone please help?

---

