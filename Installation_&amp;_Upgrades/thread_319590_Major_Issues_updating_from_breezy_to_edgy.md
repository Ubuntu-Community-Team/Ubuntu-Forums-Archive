---
title: "Major Issues updating from breezy to edgy"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by Face1 on 2006-12-15
So, I decided it would be a good idea to upgrade from DAPPER (not breezy) to edgy.  I followed the method sugested on the ubuntu website (update-manager -c) and, it mostly worked, but ended with a failure message, which I didn't write down unfortunately, and now everything is screwed up.  I restarted, and the x-server will not start...Here is the error log:```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15-26-686 i686 
Current Operating System: Linux lappy 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 15 20:40:39 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation Mobile Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg-air/modules/"
(**) Option "AIGLX" "true"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg-air/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 10cf,1378 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 10cf,137a rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 10cf,137a rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 10cf,1397 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 10cf,1389 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 10cf,138a rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 10cf,1384 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 10cf,1385 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 10cf,1387 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 10cf,1388 rev 02 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4363 card 10cf,139a rev 12 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 08:03:0: chip 1217,7134 card 3001,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:1: chip 1217,7134 card 3801,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:2: chip 1217,7120 card 10cf,131e rev 01 class 08,05,00 hdr 00
(II) PCI: 08:03:3: chip 1217,7130 card 10cf,131e rev 01 class 06,80,00 hdr 00
(II) PCI: 08:03:4: chip 1217,00f7 card 1217,00f7 rev 02 class 0c,00,10 hdr 00
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
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x8c000000 - 0x8c0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x8c100000 - 0x8c1fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,16), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xf0200000 - 0xf02fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:3:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x89ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 13: bridge is at (8:3:1), (8,13,16), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[1] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0x8a000000 - 0x8bffffff (0x2000000) MX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0300000/19, 0xe0000000/28, 0xf0400000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0380000/19
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
	[0] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[1] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[2] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[3] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[4] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[6] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[7] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[8] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[9] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[10] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[13] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[1] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[2] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[3] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[4] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[6] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[7] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[8] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[9] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[10] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[13] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[5] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[6] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[7] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[8] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[10] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[11] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[12] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[13] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[14] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[23] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[24] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[25] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[26] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg-air/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg-air/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg-air/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg-air/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg-air/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg-air/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg-air/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg-air/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg-air/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg-air/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(EE) module ABI major version (1) doesn't match the server's version (0)
(II) UnloadModule: "i810"
(II) Unloading /usr/lib/xorg-air/modules/drivers/i810_drv.so
(EE) Failed to load module "i810" (module requirement mismatch, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg-air/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg-air/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg-air/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg-air/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(EE) No drivers available.

Fatal server error:
no screens found

```


Please, please help if you can, I'd really like to be able to use my computer...

---

### Post by taurus on 2006-12-15
Boot into recovery mode from GRUB menu and configure your X again with

```
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by aysiu on 2006-12-15
I know it's a bit late to say this, but upgrading two versions at once is a recipe for breakage.

---

### Post by Face1 on 2006-12-15
Umm..I guess it's too late to say this, but I'm a fool, and meant to say that I was using dapper, not breezy....my bad....im gonna try what taurus suggested now..

---

### Post by Face1 on 2007-03-12
Okay, I've done what taurus suggested, and this allows me to start the x server using startx, but gdm refuses to start.  When the computer boots up, or I use /etc/init.d/gdm restart, xserver will not start.  This is the log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15-26-686 i686 
Current Operating System: Linux lappy 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 12 14:54:51 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation Mobile Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg-air/modules/"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg-air/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 10cf,1378 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 10cf,137a rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 10cf,137a rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 10cf,1397 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 10cf,1389 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 10cf,138a rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 10cf,1384 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 10cf,1385 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 10cf,1387 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 10cf,1388 rev 02 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4363 card 10cf,139a rev 12 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 08:03:0: chip 1217,7134 card 3001,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:1: chip 1217,7134 card 3801,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:2: chip 1217,7120 card 10cf,131e rev 01 class 08,05,00 hdr 00
(II) PCI: 08:03:3: chip 1217,7130 card 10cf,131e rev 01 class 06,80,00 hdr 00
(II) PCI: 08:03:4: chip 1217,00f7 card 1217,00f7 rev 02 class 0c,00,10 hdr 00
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
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x8c000000 - 0x8c0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x8c100000 - 0x8c1fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,16), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xf0200000 - 0xf02fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:3:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x89ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 13: bridge is at (8:3:1), (8,13,16), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[1] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0x8a000000 - 0x8bffffff (0x2000000) MX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0300000/19, 0xe0000000/28, 0xf0400000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0380000/19
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
	[0] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[1] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[2] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[3] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[4] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[6] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[7] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[8] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[9] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[10] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[13] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[1] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[2] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[3] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[4] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[6] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[7] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[8] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[9] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[10] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[13] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[14] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[15] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[16] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xf0202000 - 0xf02027ff (0x800) MX[B]
	[5] -1	0	0xf0201000 - 0xf0201fff (0x1000) MX[B]
	[6] -1	0	0xf0200000 - 0xf0200fff (0x1000) MX[B]
	[7] -1	0	0xf0202800 - 0xf02028ff (0x100) MX[B]
	[8] -1	0	0x8c100000 - 0x8c100fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xf0003fff (0x4000) MX[B]
	[10] -1	0	0xf0644400 - 0xf06447ff (0x400) MX[B]
	[11] -1	0	0xf0644000 - 0xf06443ff (0x400) MX[B]
	[12] -1	0	0xf0640000 - 0xf0643fff (0x4000) MX[B]
	[13] -1	0	0xf0380000 - 0xf03fffff (0x80000) MX[B](B)
	[14] -1	0	0xf0400000 - 0xf043ffff (0x40000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf0300000 - 0xf037ffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[23] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[24] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[25] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[26] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg-air/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg-air/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg-air/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg-air/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg-air/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg-air/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg-air/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg-air/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg-air/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(EE) module ABI major version (1) doesn't match the server's version (0)
(II) UnloadModule: "i810"
(II) Unloading /usr/lib/xorg-air/modules/drivers/i810_drv.so
(EE) Failed to load module "i810" (module requirement mismatch, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg-air/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg-air/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg-air/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg-air/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(EE) No drivers available.

Fatal server error:
no screens found

```

This seems weird to me because the i810 driver IS installed, and it appears to work fine when i just use the startx command (I get the correct resolution).  What should I do?

---

### Post by taurus on 2007-03-12
Try running these at the prompt.

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Face1 on 2007-03-12
Still getting the same error...

---

