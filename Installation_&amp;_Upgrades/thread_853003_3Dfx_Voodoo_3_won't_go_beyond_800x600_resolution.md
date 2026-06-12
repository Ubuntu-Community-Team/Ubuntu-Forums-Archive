---
title: "3Dfx Voodoo 3 won't go beyond 800x600 resolution"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2008-07-08
I've installed hardy on an older p3 with 3dfx voodoo 3 graphics board. It used to run 1600x1200 in windows, but ubuntu won't let it go beyond 800x600. I know there are hardware restrictions on this board which disallow 3d acceleration above 1024x768, but I don't need 3d acceleration. Examining the Xorg.0.log, I noticed that the video modes that I desire are all rejected. Also, dri is not loaded, which is maybe a hint?

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux dolphin 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  8 11:07:53 2008
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
(II) PCI: 00:00:0: chip 8086,7190 card 1043,8024 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:04:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:04:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:04:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 104c,9066 card 1186,3b04 rev 00 class 02,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10ec,8139 card 11f6,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:0b:1: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:0b:2: chip 1106,3104 card 0925,1234 rev 51 class 0c,03,20 hdr 80
(II) PCI: 00:0c:0: chip 1274,1371 card 1274,1371 rev 06 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 121a,0005 card 121a,003a rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xe1efffff (0x3f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe1f00000 - 0xe3ffffff (0x2100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:4:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) 3Dfx Interactive, Inc. Voodoo 3 rev 1, Mem @ 0xde000000/25, 0xe2000000/25, I/O @ 0xd800/8, BIOS @ 0xe1ff0000/16
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
(II) PCI Memory resource overlap reduced 0xe4000000 from 0xe7ffffff to 0xe3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[1] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[2] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[3] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[4] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[5] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[6] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[8] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[1] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[2] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[3] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[4] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[5] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[6] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[7] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[8] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[8] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[9] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[10] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
(II) Matched tdfx from file name tdfx.ids in autoconfig
(==) Matched tdfx for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	3dfx Voodoo3, 3dfx Voodoo5
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset 3dfx Voodoo3 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[8] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[9] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[10] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[5] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[6] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[7] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[8] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[9] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[10] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) TDFX(0): Softbooting the board (through the int10 interface).
(II) TDFX(0): Primary V_BIOS segment is: 0xc000
(II) TDFX(0): Softbooting the board succeeded.
(II) TDFX(0): TDFXFindChips: found 1 chip(s)
(II) TDFX(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) TDFX(0): Depth 24, (==) framebuffer bpp 32
(==) TDFX(0): RGB weight 888
(==) TDFX(0): Default visual is TrueColor
(--) TDFX(0): Chipset: "3dfx Voodoo3"
(--) TDFX(0): Linear framebuffer at 0xE2000000
(--) TDFX(0): MMIO registers at addr 0xDE000000
(--) TDFX(0): PIO registers at addr 0xD800
(II) TDFX(0): DRAMINIT1 read 0x40530031, programming 0x40202031 (not Banshee)
(II) TDFX(0): TDFXInitChips: numchips = 1
(II) TDFX(0): TDFXInitChips: cfgbits = 0x00000000, initbits = 0x00000001
(II) TDFX(0): TDFXInitChips: mem0base = 0xde000000, mem1base = 0xe2000008
(II) TDFX(0): TDFXInitChips: mem0size = 0x02000000, mem1size = 0x02000000
(II) TDFX(0): TDFXInitChips: mem0bits = 0x00000005, mem1bits = 0x00000050
(II) TDFX(0): TDFXInitChips: cfgbits = 0x00000055
(II) TDFX(0): TDFXInitChips: MMIOAddr[0] = 0xde000000
(II) TDFX(0): TDFXInitChips: LinearAddr[0] = 0xe2000008
(--) TDFX(0): VideoRAM: 16384 kByte Mapping 32768 kByte
(==) TDFX(0): Using gamma correction (1.0, 1.0, 1.0)
(II) TDFX(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) TDFX(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) TDFX(0): Unable to estimate virtual size
(II) TDFX(0): Clock range:  12.00 to 350.00 MHz
(II) TDFX(0): Not using default mode "640x350" (vrefresh out of range)
(II) TDFX(0): Not using default mode "320x175" (vrefresh out of range)
(II) TDFX(0): Not using default mode "640x400" (vrefresh out of range)
(II) TDFX(0): Not using default mode "320x200" (vrefresh out of range)
(II) TDFX(0): Not using default mode "720x400" (vrefresh out of range)
(II) TDFX(0): Not using default mode "360x200" (vrefresh out of range)
(II) TDFX(0): Not using default mode "640x480" (vrefresh out of range)
(II) TDFX(0): Not using default mode "320x240" (vrefresh out of range)
(II) TDFX(0): Not using default mode "640x480" (vrefresh out of range)
(II) TDFX(0): Not using default mode "320x240" (vrefresh out of range)
(II) TDFX(0): Not using default mode "640x480" (hsync out of range)
(II) TDFX(0): Not using default mode "320x240" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "400x300" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "400x300" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "400x300" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (vrefresh out of range)
(II) TDFX(0): Not using default mode "512x384" (vrefresh out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "512x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "512x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "512x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "512x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(0): Not using default mode "576x432" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x960" (hsync out of range)
(II) TDFX(0): Not using default mode "640x480" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x960" (hsync out of range)
(II) TDFX(0): Not using default mode "640x480" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "640x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "640x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "640x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "800x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(0): Not using default mode "896x672" (hsync out of range)
(II) TDFX(0): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(0): Not using default mode "896x672" (hsync out of range)
(II) TDFX(0): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(0): Not using default mode "928x696" (hsync out of range)
(II) TDFX(0): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(0): Not using default mode "928x696" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "832x624" (hsync out of range)
(II) TDFX(0): Not using default mode "416x312" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x768" (hsync out of range)
(II) TDFX(0): Not using default mode "640x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1280x800" (hsync out of range)
(II) TDFX(0): Not using default mode "640x400" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x768" (hsync out of range)
(II) TDFX(0): Not using default mode "576x384" (hsync out of range)
(II) TDFX(0): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(0): Not using default mode "576x432" (hsync out of range)
(II) TDFX(0): Not using default mode "1400x1050" (hsync out of range)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 151000 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 155800 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): rejecting mode with horizontal resolution 1400 not divisibile by 16 and clock 184000 greater than 135000
(II) TDFX(0): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(0): Not using default mode "700x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1440x900" (hsync out of range)
(II) TDFX(0): Not using default mode "720x450" (hsync out of range)
(II) TDFX(0): Not using default mode "1600x1024" (hsync out of range)
(II) TDFX(0): Not using default mode "800x512" (hsync out of range)
(II) TDFX(0): Not using default mode "1680x1050" (hsync out of range)
(II) TDFX(0): Not using default mode "840x525" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "960x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(0): Not using default mode "960x600" (hsync out of range)
(II) TDFX(0): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(0): Not using default mode "960x720" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (hsync out of range)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(0): Not using default mode "1024x768" (hsync out of range)
(--) TDFX(0): Virtual size is 800x600 (pitch 800)
(**) TDFX(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TDFX(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) TDFX(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TDFX(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) TDFX(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TDFX(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) TDFX(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) TDFX(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) TDFX(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) TDFX(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) TDFX(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) TDFX(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) TDFX(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(**) TDFX(0): ShowCache Disabled
(**) TDFX(0): video key default 0x1e
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TDFX(0): initializing int10
(II) TDFX(0): Primary V_BIOS segment is: 0xc000
(II) TDFX(0): VESA BIOS detected
(II) TDFX(0): VESA VBE Version 3.0
(II) TDFX(0): VESA VBE Total Mem: 16384 kB
(II) TDFX(0): VESA VBE OEM: 3dfx Interactive, Inc.
(II) TDFX(0): VESA VBE OEM Software Rev: 1.0
(II) TDFX(0): VESA VBE OEM Vendor: Elpin Systems, Inc.
(II) TDFX(0): VESA VBE OEM Product: 3dfx Avenger
(II) TDFX(0): VESA VBE OEM Product Rev: Version 1.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) TDFX(0): VESA VBE DDC supported
(II) TDFX(0): VESA VBE DDC Level 2
(II) TDFX(0): VESA VBE DDC transfer in appr. 8 sec.
(II) TDFX(0): VESA VBE DDC read successfully
(II) TDFX(0): Manufacturer: SAM  Model: 1cf  Serial#: 1112683057
(II) TDFX(0): Year: 2006  Week: 40
(II) TDFX(0): EDID Version: 1.3
(II) TDFX(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) TDFX(0): Sync:  Separate  Composite  SyncOnGreen
(II) TDFX(0): Max H-Image Size [cm]: horiz.: 43  vert.: 32
(II) TDFX(0): Gamma: 2.20
(II) TDFX(0): DPMS capabilities: Off; RGB/Color Display
(II) TDFX(0): First detailed timing is preferred mode
(II) TDFX(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) TDFX(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) TDFX(0): Supported VESA Video Modes:
(II) TDFX(0): 720x400@70Hz
(II) TDFX(0): 640x480@60Hz
(II) TDFX(0): 640x480@67Hz
(II) TDFX(0): 640x480@72Hz
(II) TDFX(0): 640x480@75Hz
(II) TDFX(0): 800x600@56Hz
(II) TDFX(0): 800x600@60Hz
(II) TDFX(0): 800x600@72Hz
(II) TDFX(0): 800x600@75Hz
(II) TDFX(0): 832x624@75Hz
(II) TDFX(0): 1024x768@60Hz
(II) TDFX(0): 1024x768@70Hz
(II) TDFX(0): 1024x768@75Hz
(II) TDFX(0): 1280x1024@75Hz
(II) TDFX(0): 1152x870@75Hz
(II) TDFX(0): Manufacturer's mask: 0
(II) TDFX(0): Supported Future Video Modes:
(II) TDFX(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) TDFX(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) TDFX(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) TDFX(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) TDFX(0): Supported additional Video Mode:
(II) TDFX(0): clock: 162.0 MHz   Image Size:  432 x 324 mm
(II) TDFX(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) TDFX(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) TDFX(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 170 MHz
(II) TDFX(0): Monitor name: SyncMaster
(II) TDFX(0): Serial No: HS8LA00501
(II) TDFX(0): EDID (in hex):
(II) TDFX(0): 	00ffffffffffff004c2dcf0131325242
(II) TDFX(0): 	281001030e2b20782aee95a3544c9926
(II) TDFX(0): 	0f5054bfef80a94081808140714f0101
(II) TDFX(0): 	010101010101483f403062b0324040c0
(II) TDFX(0): 	1300b0441100001e000000fd00384b1e
(II) TDFX(0): 	5111000a202020202020000000fc0053
(II) TDFX(0): 	796e634d61737465720a2020000000ff
(II) TDFX(0): 	004853384c4130303530310a2020004d
(II) TDFX(0): EDID vendor "SAM", prod id 463
(II) TDFX(0): Using hsync ranges from config file
(II) TDFX(0): Using vrefresh ranges from config file
(II) TDFX(0): Printing DDC gathered Modelines:
(II) TDFX(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) TDFX(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) TDFX(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) TDFX(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) TDFX(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) TDFX(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) TDFX(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) TDFX(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) TDFX(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) TDFX(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) TDFX(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) TDFX(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B]
	[1] 0	0	0xde000000 - 0xdfffffff (0x2000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xdd000000 - 0xdd01ffff (0x20000) MX[B]
	[9] -1	0	0xdd800000 - 0xdd801fff (0x2000) MX[B]
	[10] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[11] -1	0	0xe1ff0000 - 0xe1ffffff (0x10000) MX[B](B)
	[12] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B](B)
	[13] -1	0	0xde000000 - 0xdfffffff (0x2000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a03f (0x40) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprD)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprD)
(==) TDFX(0): Write-combining range (0xe2000000,0x2000000)
(II) TDFX(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0xd500
(II) TDFX(0): Changing back offset from 0x00bd7000 to 0x00bd6000
(II) TDFX(0): Textures Memory 8.43 MB
(II) TDFX(0): Cursor Offset: [0x00000000,0x00001000)
(II) TDFX(0): Fifo Offset: [0x00001000, 0x00041000)
(II) TDFX(0): Front Buffer Offset: [0x00041000, 0x00367400)
(II) TDFX(0): Texture Offset: [0x00367400, 0x00BD6000)
(II) TDFX(0): BackOffset: [0x00BD6000, 0x00DEA000)
(II) TDFX(0): DepthOffset: [0x00DEB000, 0x00FFF000)
(II) TDFX(0): Minimum 432, Maximum 1447 lines of offscreen memory available
(EE) TDFX(0): [dri] tdfx DRI not supported in 32 bpp mode, disabling DRI.
(II) TDFX(0): [dri] To use DRI, invoke the server using 16 bpp
	(-depth 15 or -depth 16).
(II) TDFX(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Driver provided NonTEGlyphRenderer replacement
	Setting up tile and stipple cache:
		32 128x128 slots
		8 256x256 slots
(==) TDFX(0): Backing store disabled
(==) TDFX(0): Silken mouse enabled
(II) TDFX(0): DPMS enabled
(WW) TDFX(0): Direct rendering disabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "be"
(**) Generic Keyboard: XkbLayout: "be"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled

```

---

### Post by overdrank on 2008-07-08
HI and I know some users have been able to get this graphics card to work in earlier versions of ubuntu, but Hardy has changed the xorg greatly. Oh and please use the code tags on your post with that much data it will save space. They are on the message reply #
```
then insert data here
```
If you can use the alt F2 keys and enter this command ```
gksu displayconfig-gtk
``` YOu may be able to set your resolution. It has helped some to change the default depth in the xorg from 24 to 16.

---

### Post by Kusho on 2008-08-10
Okay this is my question also.  On a google quest.  I have a shitty Rage 3d that also works for this computer, and I can get better resolutions out of it, but your telling me that ubuntu basically don't have any support for this card???  And if I want to run it I need to get rid of linux???  and go back to windows 98 or me?

That's a sad answer.
---

Posted a new forum and got answer 
[http://ubuntuforums.org/search.php?searchid=46114123](http://ubuntuforums.org/search.php?searchid=46114123)

---

### Post by hikaricore on 2008-09-13
> **Kusho said:**
> Okay this is my question also.  On a google quest.  I have a shitty Rage 3d that also works for this computer, and I can get better resolutions out of it, but your telling me that ubuntu basically don't have any support for this card???  And if I want to run it I need to get rid of linux???  and go back to windows 98 or me?

That's a sad answer.


This is an example of the kind of post decent people don't respond with to a thread they didn't start.

---

### Post by twodogsdad on 2009-01-05
Hi. I also have an old machine with a 3dfx voodoo3 card in it. Has this question/thread been solved? If so, how?

I'm just trying to take a free, old Compaq from one friend and install Xubuntu on it and give it to another who needs something for internet and word processing, hence I don't want to spend money and I don't have access to another video card to drop in there.

Thanks,
Cal:popcorn:

---

### Post by twodogsdad on 2009-01-05
Hi. I also have an old machine with a 3dfx voodoo3 card in it. Has this question/thread been solved? If so, how?

I'm just trying to take a free, old Compaq from one friend and install Xubuntu on it and give it to another who needs something for internet and word processing, hence I don't want to spend money and I don't have access to another video card to drop in there.

Thanks,
Cal:popcorn:

Oooops, don't know how this got duplicated.

---

### Post by twodogsdad on 2009-01-05
I think I found my solution on 

[http://ubuntuforums.org/showthread.php?t=907272&highlight=3dfx+voodoo3&page=1](http://ubuntuforums.org/showthread.php?t=907272&highlight=3dfx+voodoo3&page=1)

Thanks...

---

