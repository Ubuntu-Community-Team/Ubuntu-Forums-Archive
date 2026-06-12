---
title: "Can only boot to CLI, not GUI after upgrade from Hardy to Ibex"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by The Developer on 2008-10-31
After doing a network upgrade to Ibex, the system fails to initialize X, and so I'm left with just a CLI login prompt on bootup. It seems that the "cleaning obsolete packages" stage of the upgrade completely wiped out EVERY package I have, rather than just the 'obsolete' ones.

Anyway, for some reason the X window manager can't start, and I believe it's because it can't find the 'nv' driver. Here is the log:

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux TheLegend-UbuntuStyle 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 31 15:36:07 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x7bd660
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card f043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,04,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0092 card 1682,2182 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:0c:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd3000000 - 0xd4ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7800 GT] rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0x9000/7, BIOS @ 0xd2000000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd4000000 - 0xd4003fff (0x4000) MX[B]
	[1] -1	0	0xd4004000 - 0xd4007fff (0x4000) MX[B]
	[2] -1	0	0xd4008000 - 0xd40087ff (0x800) MX[B]
	[3] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[4] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[5] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[6] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[8] -1	0	0xd5004000 - 0xd5004fff (0x1000) MX[B]
	[9] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd4000000 - 0xd4003fff (0x4000) MX[B]
	[1] -1	0	0xd4004000 - 0xd4007fff (0x4000) MX[B]
	[2] -1	0	0xd4008000 - 0xd40087ff (0x800) MX[B]
	[3] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[4] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[5] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[6] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[8] -1	0	0xd5004000 - 0xd5004fff (0x1000) MX[B]
	[9] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[10] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
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
	[4] -1	0	0xd4000000 - 0xd4003fff (0x4000) MX[B]
	[5] -1	0	0xd4004000 - 0xd4007fff (0x4000) MX[B]
	[6] -1	0	0xd4008000 - 0xd40087ff (0x800) MX[B]
	[7] -1	0	0xd5000000 - 0xd5000fff (0x1000) MX[B]
	[8] -1	0	0xd5001000 - 0xd5001fff (0x1000) MX[B]
	[9] -1	0	0xd5002000 - 0xd5002fff (0x1000) MX[B]
	[10] -1	0	0xd5003000 - 0xd5003fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xd5004000 - 0xd5004fff (0x1000) MX[B]
	[13] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "nv"
(WW) Warning, couldn't open module nv
(II) UnloadModule: "nv"
(EE) Failed to load module "nv" (module does not exist, 0)
(II) LoadModule: "mouse"
(WW) Warning, couldn't open module mouse
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(EE) No drivers available.

Fatal server error:
no screens found

```

And here's my xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

As you can see, it "Failed to load module "nv" (module does not exist, 0)". How do I resolve this??

Many thanks.

---

### Post by mootpoint on 2008-10-31
This may or may not be helpful. I had used envy to install my NVidia drivers in 8.04. When I rebooted into 8.10, my video driver world was a mess. 

I ended up using envyng -t (terminal mode) to remove all drivers I'd installed via envy, was able to get a low-res only type GUI, and loaded the closed nvidia driver via system/administration/hardware drivers. I'm still not sure it's quite right, but at least I get Gnome in a usable resolution now.

You may want to try the same technique and see if you get anywhere. If you can get network access and a terminal, you can always put it back the same way you take it out.

m00t

---

### Post by invisibleidiot on 2008-11-01
I have a sort of similar, but stranger problem. I upgraded my Dell m1330 laptop from Hardy (which was running fine for about 3 months) to Ibex last night. When it was doing the upgrade, it asked me if I wanted to keep a blacklist file and a fs file. I'm a novice to linux, but I knew I had made changes to the blacklist file to get certain things running on my Dell, so I kept the old one and let ubuntu change the fs file. When the system rebooted, I noticed two things... the fan was CRANKING on high the whole time. In fact, I dont think I had ever heard the fan run that hard before! It let me log in OK from the graphical prompt, and it seemed to load xwindows OK. However, I could not move any of the windows that opened (it was asking me for the wep key for my router) and I couldnt type anything in. I tried typing the wep key in, nothing showed up. I opened a terminal window (I had an icon on my top menu bar), but I could not type anything in there either. Wierd. Right now, I'm using my Vista partition to do all this (YUCK!). Anyone have any ideas?
Thanks in advance!

---

### Post by Noxn on 2008-11-01
Same, here:
[http://ubuntuforums.org/showthread.php?p=6081755](http://ubuntuforums.org/showthread.php?p=6081755) (read everything)

It uninstalled EVERY SINGLE PROGRAM on my linux box... Even stuff the SYSTEM needs.

How could i know what the system wanted from me? it told me they where obsolete, so i thought it would be upgraded or something...

I can only boot into cli, have only internet with help of some commands (thread above).


I dont know, but is there ANY WAY of fixing this without reinstall?

---

### Post by horned0wl93 on 2008-11-01
> **The Developer said:**
> After doing a network upgrade to Ibex, the system fails to initialize X, and so I'm left with just a CLI login prompt on bootup. It seems that the "cleaning obsolete packages" stage of the upgrade completely wiped out EVERY package I have, rather than just the 'obsolete' ones.

Anyway, for some reason the X window manager can't start, and I believe it's because it can't find the 'nv' driver. Here is the log:

[CODE]
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux TheLegend-UbuntuStyle 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

As you can see, it "Failed to load module "nv" (module does not exist, 0)". How do I resolve this??

Many thanks.

This entry is identical to mine, except that I have an ATI Radeon 200M (X1100) video driver, and my system fails to start fglrx.  I can't find it on the system or install it from anywhere in the multiverse.  Why is 8.10 killing restricted drivers?  Any help most appreciated.

Cheers;
Ed

---

