---
title: "Startx doesn't work"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by mckswk on 2005-02-25
Hi

I have installed Ubuntu,but I'm unable to run startx:(
When I'm running Ubuntu form Live CD everything is working properly.
I've Sony Vaio Laptop GRT915M with GeForceMX64 graphics card.
It's first time I have installed Linux so I'm totally lost.

Here is full log file:

This is a pre-release version of XFree86, and is not supported in any
way.  Bugs may be reported to [email]XFree86@XFree86.Org[/email] and patches submitted
to [email]fixes@XFree86.Org[/email].  Before reporting bugs in pre-release versions,
please check the latest version in the XFree86 CVS repository
([http://www.XFree86.Org/cvs)](http://www.XFree86.Org/cvs)).

XFree86 Version 4.3.0.1 (Ubuntu 4.3.0.dfsg.1-6ubuntu25 20041018053958 [email]root@macaroni.warthogs.hbd.com[/email])
Release Date: 15 August 2003
X Protocol Version 11, Revision 0, Release 6.6
Build Operating System: Linux 2.6.8.1 i686 [ELF] 
Build Date: 18 October 2004
	Before reporting problems, check [http://www.XFree86.Org/](http://www.XFree86.Org/)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004 TF
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Fri Feb 25 17:58:37 2005
(==) Using config file: "/etc/X11/XF86Config-4"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Silicon Integrated Systems (SiS) SG86C202"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xfree86"
(**) XKB: rules: "xfree86"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "gb"
(**) XKB: layout: "gb"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/Speedo,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(--) using VT number 7

(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	XFree86 ANSI C Emulation: 0.2
	XFree86 Video Driver: 0.6
	XFree86 XInput driver : 0.4
	XFree86 Server Extension : 0.2
	XFree86 Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) PCI: Probing config type using method 1
(II) PCI: Config type is 1
(II) PCI: stages = 0x03, oldVal1 = 0x00000000, mode1Res1 = 0x80000000
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0648 card 104d,814e rev 03 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 14 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 104d,814e rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:6: chip 1039,7013 card 104d,814e rev a0 class 07,03,00 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 104d,814e rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 104d,814e rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 104d,814e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 104d,814e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 104d,814e rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 104d,814e rev 90 class 02,00,00 hdr 00
(II) PCI: 00:07:0: chip 168c,0013 card 1468,0406 rev 01 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 1180,0476 card 4000,0000 rev aa class 06,07,00 hdr 82
(II) PCI: 00:0a:1: chip 1180,0476 card 4800,0000 rev aa class 06,07,00 hdr 82
(II) PCI: 00:0a:2: chip 1180,0552 card 104d,814e rev 02 class 0c,00,10 hdr 80
(II) PCI: 01:00:0: chip 10de,031a card 104d,814f rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x20800000 - 0x20bfffff (0x400000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20400000 - 0x207fffff (0x400000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:10:1), (0,6,9), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x21000000 - 0x213fffff (0x400000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x20c00000 - 0x20ffffff (0x400000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation GeForce FX Go5600 rev 161, Mem @ 0xd5000000/24, 0xe0000000/28
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd4005000 - 0xd40057ff (0x800) MX[B]
	[1] -1	0	0xd4010000 - 0xd401ffff (0x10000) MX[B]
	[2] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[3] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[4] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[7] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[11] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[14] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[16] -1	0	0x00001020 - 0x0000103f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd4005000 - 0xd40057ff (0x800) MX[B]
	[1] -1	0	0xd4010000 - 0xd401ffff (0x10000) MX[B]
	[2] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[3] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[4] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[7] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[11] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[12] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[13] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[14] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[16] -1	0	0x00001020 - 0x0000103f (0x20) IX[B]
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
	[5] -1	0	0xd4005000 - 0xd40057ff (0x800) MX[B]
	[6] -1	0	0xd4010000 - 0xd401ffff (0x10000) MX[B]
	[7] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[8] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[9] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[10] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[11] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd5000000 - 0xd5ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00001480 - 0x000014ff (0x80) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[21] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[22] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[23] -1	0	0x00001020 - 0x0000103f (0x20) IX[B]
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_vertex.o":  No symbols found
(II) Module GLcore: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
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
(II) Module freetype: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 2.0.2
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Reloading /usr/X11R6/lib/modules/extensions/libGLcore.a
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.13.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "speedo"
(II) Loading /usr/X11R6/lib/modules/fonts/libspeedo.a
Skipping "/usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o":  No symbols found
(II) Module speedo: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.1
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Speedo
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.2
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "v4l"
(II) Loading /usr/X11R6/lib/modules/drivers/linux/v4l_drv.o
(II) Module v4l: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.0.1
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "xtt"
(II) Loading /usr/X11R6/lib/modules/fonts/libxtt.a
(II) Module xtt: vendor="X-TrueType Server Project & After X-TT Project"
	compiled for 4.3.0.1, module version = 1.4.1
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font xtt
(II) LoadModule: "sis"
(II) Loading /usr/X11R6/lib/modules/drivers/sis_drv.o
(II) Module sis: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.7.0
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/661FX/M661FX/M661MX/741/741GX/M741/760/M760, SIS340
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found

When reporting a problem related to a server crash, please send
the full server output, not just the last messages.
This can be found in the log file "/var/log/XFree86.0.log".
Please report problems to [email]debian-x@lists.debian.org[/email].

---

### Post by alastair on 2005-02-25
It looks like it is loading the wrong graphics driver ((II) LoadModule: "sis"). Assuming you really have an NVidia graphics chip.

You need to change the "Driver" line from "sis" (or whatever) to :

Driver "nv"

in the file /etc/X11/XF86Config-4 (or XF86Config)

---

### Post by mckswk on 2005-02-25
Thanks a lot!I've changed to driver to "nv" and startx is working now.But there is problem with resolution: when it's more than 800x600 the screen is indistinct.In device mangager system still  see that sis graphics card.

---

