---
title: "Fglrx"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by dado on 2005-04-21
FGLRX Driver doesnt work
This is my Log please HELP ME

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
OS Kernel: Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004 T
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/XFree86.0.log", Time: Fri Apr 22 12:02:08 2005
(==) Using config file: "/etc/X11/XF86Config-4"
(==) ServerLayout "Server Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "ATI Graphics Adapter"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xfree86"
(**) XKB: rules: "xfree86"
(**) Option "XkbModel" "pc101"
(**) XKB: model: "pc101"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(++) using VT number 7

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
(II) PCI: 00:00:0: chip 1106,3148 card 1106,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 14f1,2f00 card 14f1,2004 rev 01 class 07,80,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1106,4161 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1106,0102 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4150 card 1458,4024 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4170 card 1458,4025 rev 00 class 03,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x9fc00000 - 0xdfcfffff (0x40100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4150) rev 0, Mem @ 0xc0000000/28, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4170) rev 0, Mem @ 0xb0000000/28, 0xdfee0000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[1] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[9] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[14] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[1] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[1] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[2] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[5] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[9] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[14] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[1] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
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
	[5] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[6] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[7] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[10] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.2
	Module class: XFree86 Font Renderer
	ABI class: XFree86 Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
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
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_vertex.o":  No symbols found
(II) Module GLcore: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Server Extension, version 0.2
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.0.1, module version = 8.12.10
	Module class: XFree86 Video Driver
	ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.4

---

### Post by dado on 2005-04-21
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), FireGL V3100 (RV370 5B64),
	MOBILITY RADEON X300 (M22 5460), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835)
(II) Primary Device is: PCI 01:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 (RV350 4150) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[6] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[7] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[10] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81fa400
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[6] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[7] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[10] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	ABI class: XFree86 Video Driver, version 0.6

---

### Post by dado on 2005-04-21
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000800"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "0x00000000"
(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "IgnoreEDID" "off"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "NoTV" "yes"
(**) fglrx(0): Option "TVStandard" "NTSC-M"
(**) fglrx(0): Option "TVHSizeAdj" "0"
(**) fglrx(0): Option "TVVSizeAdj" "0"
(**) fglrx(0): Option "TVHPosAdj" "0"
(**) fglrx(0): Option "TVVPosAdj" "0"
(**) fglrx(0): Option "TVHStartAdj" "0"
(**) fglrx(0): Option "TVColorAdj" "0"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON 9600 (RV350 4150)" (Chipset = 0x4150)
(--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0x4024)
(--) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(--) fglrx(0): ROM-BIOS at 0xdfec0000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x0C
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 Video Driver, version 0.6
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.2.0
	ABI class: XFree86 Video Driver, version 0.6
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 0
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 1
(II) fglrx(0): Primary head:
 Monitor   -- CRT
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): EDID data from the display on Secondary head ---------------------------
(II) fglrx(0): Manufacturer: PTS  Model: 304  Serial#: 180182
(II) fglrx(0): Year: 2003  Week: 9
(II) fglrx(0): EDID Version: 1.1
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 1.27
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.618 redY: 0.349   greenX: 0.280 greenY: 0.605
(II) fglrx(0): blueX: 0.152 blueY: 0.063   whiteX: 0.281 whiteY: 0.310
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 100  vid: 26693
(II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 40.5 MHz   Image Size:  310 x 230 mm
(II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 720 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 480  v_sync: 481  v_sync_end 484 v_blanking: 506 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 56.2 MHz   Image Size:  270 x 200 mm
(II) fglrx(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) fglrx(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) fglrx(0):  FAVJ320180182
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(**) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Overlay disabled
(**) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Validating mode for clone (secondary) head ------------
(II) fglrx(0): Total 0 valid mode(s) found.
(II) fglrx(0): Monitor0: Using hsync range of 30.00-70.00 kHz
(II) fglrx(0): Monitor0: Using vrefresh range of 50.00-160.00 Hz
(II) fglrx(0): Clock range:  20.00 to 400.00 MHz
(II) fglrx(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1280x960" (hsync out of range)
(II) fglrx(0): Not using default mode "640x480" (hsync out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1152x864" (hsync out of range)
(II) fglrx(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,Monitor0) mode clock 122MHz exceeds DDC maximum 110MHz
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "960x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1280x960" (width too large for virtual size)
(--) fglrx(0): Virtual size is 1152x864 (pitch 1152)
(**) fglrx(0): *Default mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) fglrx(0): *Default mode "800x600": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) fglrx(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) fglrx(0): *Default mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) fglrx(0): *Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) fglrx(0):  Default mode "1400x1050": 122.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) fglrx(0):  Default mode "1152x768": 65.0 MHz (scaled from 0.0 MHz), 44.2 kHz, 54.8 Hz
(II) fglrx(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) fglrx(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 87.1 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) fglrx(0):  Default mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) fglrx(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 61.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 54.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 54.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.0 Hz
(II) fglrx(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) fglrx(0):  Default mode "640x400": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) fglrx(0):  Default mode "576x432": 54.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x350": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) fglrx(0):  Default mode "576x384": 32.5 MHz (scaled from 0.0 MHz), 44.2 kHz, 54.8 Hz (D)
(II) fglrx(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 47.2 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 39.4 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 37.5 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 32.5 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 22.4 MHz (scaled from 0.0 MHz), 35.5 kHz, 87.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) fglrx(0):  Default mode "416x312": 28.6 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.7 Hz (D)
(II) fglrx(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 28.1 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 25.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz (D)
(II) fglrx(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 20.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync

---

### Post by dado on 2005-04-21
(II) fglrx(0): Valid Clone Mode: 1024x768
(II) fglrx(0): Valid Clone Mode: 800x600
(II) fglrx(0): Valid Clone Mode: 640x480
(II) fglrx(0): Valid Clone Mode: 1152x864
(II) fglrx(0): Valid Clone Mode: 1152x768
(II) fglrx(0): Valid Clone Mode: 1024x768
(II) fglrx(0): Valid Clone Mode: 1024x768
(II) fglrx(0): Valid Clone Mode: 1024x768
(II) fglrx(0): Valid Clone Mode: 1024x768
(II) fglrx(0): Valid Clone Mode: 832x624
(II) fglrx(0): Valid Clone Mode: 800x600
(II) fglrx(0): Valid Clone Mode: 800x600
(II) fglrx(0): Valid Clone Mode: 800x600
(II) fglrx(0): Valid Clone Mode: 800x600
(II) fglrx(0): Valid Clone Mode: 700x525
(II) fglrx(0): Valid Clone Mode: 640x512
(II) fglrx(0): Valid Clone Mode: 640x480
(II) fglrx(0): Valid Clone Mode: 640x480
(II) fglrx(0): Valid Clone Mode: 640x480
(II) fglrx(0): Valid Clone Mode: 640x480
(II) fglrx(0): Valid Clone Mode: 720x400
(II) fglrx(0): Valid Clone Mode: 640x400
(II) fglrx(0): Valid Clone Mode: 576x432
(II) fglrx(0): Valid Clone Mode: 640x350
(II) fglrx(0): Valid Clone Mode: 576x384
(II) fglrx(0): Valid Clone Mode: 512x384
(II) fglrx(0): Valid Clone Mode: 512x384
(II) fglrx(0): Valid Clone Mode: 512x384
(II) fglrx(0): Valid Clone Mode: 512x384
(II) fglrx(0): Valid Clone Mode: 512x384
(II) fglrx(0): Valid Clone Mode: 416x312
(II) fglrx(0): Valid Clone Mode: 400x300
(II) fglrx(0): Valid Clone Mode: 400x300
(II) fglrx(0): Valid Clone Mode: 400x300
(II) fglrx(0): Valid Clone Mode: 400x300
(II) fglrx(0): Total of 35 clone modes found ------------

(II) fglrx(0): Validating modes on Primary head ---------
(II) fglrx(0): Monitor0: Using hsync range of 30.00-70.00 kHz
(II) fglrx(0): Monitor0: Using vrefresh range of 50.00-160.00 Hz
(II) fglrx(0): Clock range:  20.00 to 400.00 MHz
(II) fglrx(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1280x960" (hsync out of range)
(II) fglrx(0): Not using default mode "640x480" (hsync out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1280x1024" (hsync out of range)
(II) fglrx(0): Not using default mode "640x512" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1600x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "800x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "896x672" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "928x696" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "1152x864" (hsync out of range)
(II) fglrx(0): Not using default mode "576x432" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (hsync out of range)
(II) fglrx(0): Not using default mode "700x525" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1200" (hsync out of range)
(II) fglrx(0): Not using default mode "960x600" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1280x960" (width too large for virtual size)
(--) fglrx(0): Virtual size is 1152x864 (pitch 1152)
(**) fglrx(0): *Default mode "1024x768": 94.5 MHz (scaled from -342679.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) fglrx(0): *Default mode "800x600": 56.3 MHz (scaled from 1272948.2 MHz), 53.7 kHz, 85.1 Hz
(II) fglrx(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) fglrx(0): *Default mode "640x480": 36.0 MHz (scaled from 73977.9 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) fglrx(0): *Default mode "1152x864": 108.0 MHz (scaled from 221933.6 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) fglrx(0):  Default mode "1152x768": 65.0 MHz (scaled from 1720909.2 MHz), 44.2 kHz, 54.8 Hz
(II) fglrx(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 782313.5 MHz), 60.1 kHz, 75.1 Hz
(II) fglrx(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from -203793.4 MHz), 56.5 kHz, 70.1 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from -1894607.9 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from -1685372.4 MHz), 35.5 kHz, 87.1 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) fglrx(0):  Default mode "832x624": 57.3 MHz (scaled from 1844769.3 MHz), 49.7 kHz, 74.6 Hz
(II) fglrx(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 638590.5 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from -135862.3 MHz), 48.1 kHz, 72.2 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from -1826676.7 MHz), 37.9 kHz, 60.3 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 73977.9 MHz), 35.2 kHz, 56.2 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 61.0 MHz (scaled from 6046.7 MHz), 64.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 54.0 MHz (scaled from -2036516.9 MHz), 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from -1545882.1 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from -1545882.1 MHz), 37.9 kHz, 72.8 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 1340274.7 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 54.0 MHz (scaled from -2036516.9 MHz), 60.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x400": 35.5 MHz (scaled from 848430.6 MHz), 37.9 kHz, 85.0 Hz
(II) fglrx(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) fglrx(0):  Default mode "640x400": 31.5 MHz (scaled from -1545882.1 MHz), 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) fglrx(0):  Default mode "576x432": 54.0 MHz (scaled from -2036516.9 MHz), 67.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x350": 31.5 MHz (scaled from -1545882.1 MHz), 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) fglrx(0):  Default mode "576x384": 32.5 MHz (scaled from 792509.6 MHz), 44.2 kHz, 54.8 Hz (D)
(II) fglrx(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 47.2 MHz (scaled from -171339.5 MHz), 68.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 39.4 MHz (scaled from -1756326.9 MHz), 60.1 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 37.5 MHz (scaled from 2045586.9 MHz), 56.5 kHz, 70.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 32.5 MHz (scaled from 1200179.7 MHz), 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 22.4 MHz (scaled from 1304797.4 MHz), 35.5 kHz, 87.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) fglrx(0):  Default mode "416x312": 28.6 MHz (scaled from 922384.6 MHz), 49.7 kHz, 74.7 Hz (D)
(II) fglrx(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 28.1 MHz (scaled from -1511009.5 MHz), 53.7 kHz, 85.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 319295.2 MHz), 46.9 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 25.0 MHz (scaled from -67931.1 MHz), 48.1 kHz, 72.2 Hz (D)
(II) fglrx(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 20.0 MHz (scaled from -913338.4 MHz), 37.9 kHz, 60.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(==) fglrx(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
(II) Module fb: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.0.0
	ABI class: XFree86 ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 0.1.0
	ABI class: XFree86 Video Driver, version 0.6
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="The XFree86 Project"
	compiled for 4.3.0.1, module version = 1.1.0
	ABI class: XFree86 Video Driver, version 0.6
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.0.1, module version = 8.12.10
	ABI class: XFree86 Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x000006a4
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffefe00 - 0xdffefeff (0x100) MX[B]
	[8] -1	0	0xdffeff00 - 0xdffeffff (0x100) MX[B]
	[9] -1	0	0xdfff0000 - 0xdfffffff (0x10000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[12] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[15] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM area:     0xc05cd000 (size=0x07a33000)
(II) fglrx(0): driver needs XFree86 4.3.x
(II) fglrx(0): detected XFree86 4.3.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xd0a22000
(II) fglrx(0): [drm] mapped SAREA 0xd0a22000 to 0x4023a000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 3.12.0
(II) fglrx(0):     Date: Jul 16 2004
(II) fglrx(0):     Desc: ATI Fire GL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xd0a22000 at 0x4023a000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1152,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1152,864) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 864)
(II) fglrx(0): Largest offscreen area available: 1152 x 7323
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(**) Option "Protocol" "ImPS/2"
(**) Mouse1: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Mouse1: Core Pointer
(**) Option "Device" "/dev/mouse"
(EE) xf86OpenSerial: Cannot open device /dev/mouse
	No such file or directory.
(EE) Mouse1: cannot open input device
(EE) PreInit failed for input device "Mouse1"
(II) UnloadModule: "mouse"
(II) Keyboard "Keyboard1" handled by legacy driver
(WW) No core pointer registered
No core pointer

Fatal server error:
failed to initialize core devices

When reporting a problem related to a server crash, please send
the full server output, not just the last messages.
This can be found in the log file "/var/log/XFree86.0.log".
Please report problems to [email]debian-x@lists.debian.org[/email].

---

### Post by dado on 2005-04-21
Sorry for this but i canot do this else
 here is also atachment

---

