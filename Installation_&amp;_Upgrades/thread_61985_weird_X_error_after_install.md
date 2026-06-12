---
title: "weird X error after install"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by lvraab on 2005-09-02
I just got my Hoary CD, I installed, so on and so forth. After my reboot I was given the following error message about a failure to load X:

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 31 20:00:12 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "E151FP"
(**) |   |-->Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 1028,0160 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1028,0160 rev 01 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 1028,0160 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1028,0160 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1028,0160 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,0160 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1028,0160 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1028,0160 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:04:0: chip 10de,0322 card 1554,1152 rev a1 class 03,00,00 hdr 00
(II) PCI: 01:05:0: chip 14e4,4212 card 1028,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:06:0: chip 1102,0006 card 1102,1003 rev 00 class 04,01,00 hdr 80
(II) PCI: 01:06:1: chip 1102,7004 card 1102,1003 rev 00 class 09,80,00 hdr 80
(II) PCI: 01:09:0: chip 14e4,4401 card 1028,8127 rev 01 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfeafffff (0x1b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corp. 82845G/GL [Brookdale-G] Chipset Integrated Graphics Device rev 1, Mem @ 0xe0000000/27, 0xfeb80000/19
(--) PCI:*(1:4:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xf0000000/27, BIOS @ 0xfea00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[1] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[2] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000df98 - 0x0000df9f (0x8) IX[B]
	[9] -1	0	0x0000dfe0 - 0x0000dfff (0x20) IX[B]
	[10] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[11] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[14] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[15] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[1] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[2] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000df98 - 0x0000df9f (0x8) IX[B]
	[9] -1	0	0x0000dfe0 - 0x0000dfff (0x20) IX[B]
	[10] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[11] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[14] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[15] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[6] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df98 - 0x0000df9f (0x8) IX[B]
	[18] -1	0	0x0000dfe0 - 0x0000dfff (0x20) IX[B]
	[19] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 01:04:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:0) found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

From what I can tell, it's not using my video card to display graphics.  ](*,) Any help appreciated. I can login, but obviously only to a command prompt.

---

### Post by DarkAlpha on 2005-09-03
I have an almost identical XOrg log - i.e. a similar error.

I'm trying to get ATI drivers installed on my laptop but am not having much luck. I've followed instructions at [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) but setting "Driver		"fglrx"" causes X not to start and gives the same XOrg.0.log as shown above. If I change Driver to "ati" everything works fine again.

Obivously, I would like to have fglrx and the 3D enabled drivers working.

(Hardware: Acer 5014WLMI, GFX - Ati Radeon X700 Mobility, Architecture AMD64, Ubuntu 5.04)

---

### Post by alpage2 on 2005-09-07
You may be able to fix this by generating a new xorg.conf file, provided that you know the model of your graphics card, and the horizontal and vertical frequencies of your monitor.

At the command line, run xorgconfig, and answer the prompts for this type of information. It will start with mouse and keyboard details.

CTRL C will drop you back to the command line if you need to break off.

You will probably need root permissions to edit this file.

Hope that helps

Alan

---

### Post by XDevHald on 2005-09-07
[QUOTE=alpage2]You may be able to fix this by generating a new xorg.conf file, provided that you know the model of your graphics card, and the horizontal and vertical frequencies of your monitor.

At the command line, run xorgconfig, and answer the prompts for this type of information. It will start with mouse and keyboard details.

CTRL C will drop you back to the command line if you need to break off.

You will probably need root permissions to edit this file.

Hope that helps

Alan[/QUOTE]
 Agreed with the above post. I have the same issue and will follow up on this if the problem has been fixed.

---

### Post by XDevHald on 2005-09-07
Interesting, the command does not even work? anyone else running into this problem?

---

### Post by Thulemanden on 2005-09-12
[QUOTE=Steve Myers]Interesting, the command does not even work? anyone else running into this problem?[/QUOTE]


The command xorgconfig works fine here as root.

---

