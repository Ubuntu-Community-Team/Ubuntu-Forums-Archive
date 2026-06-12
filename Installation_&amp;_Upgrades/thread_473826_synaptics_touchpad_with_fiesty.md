---
title: "synaptics touchpad with fiesty"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by sxauer on 2007-06-14
I upgraded from edgy to fiesty...everything worked great in edgy (should have left well enough alone)  Now my touchpad doesnt work....it was working prior to the upgrade....I have to use a usb mouse to get anything done.  I've searched high and low to find a fix and can not find one. Can anyone help me out?  Logfiles as follows

xorg.0.log
--------------

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux sexauer-laptop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 14 11:07:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
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

____cut to shorten_____

(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.1.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
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
(II) SAVAGE: driver (version 2.1.2) for S3 Savage chipsets: Savage4,
	Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
	Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
	Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
	SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
	SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
	SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01:00:0
(--) Chipset ProSavageDDR found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0000100 - 0xf00001ff (0x100) MX[B]
	[5] -1	0	0xf0000000 - 0xf00000ff (0x100) MX[B]
	[6] -1	0	0xf0001000 - 0xf0001fff (0x1000) MX[B]
	[7] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[8] -1	0	0x98000000 - 0x9800ffff (0x10000) MX[B](B)
	[9] -1	0	0x90000000 - 0x97ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e300 - 0x0000e3ff (0x100) IX[B]
	[14] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[15] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[16] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[17] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[18] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0000100 - 0xf00001ff (0x100) MX[B]
	[5] -1	0	0xf0000000 - 0xf00000ff (0x100) MX[B]
	[6] -1	0	0xf0001000 - 0xf0001fff (0x1000) MX[B]
	[7] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[8] -1	0	0x98000000 - 0x9800ffff (0x10000) MX[B](B)
	[9] -1	0	0x90000000 - 0x97ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e300 - 0x0000e3ff (0x100) IX[B]
	[17] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[18] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[19] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[20] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[21] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x864" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x960" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x960" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x768" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 640x384 60Hz.
(II) SAVAGE(0): Not using default mode "640x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x800" (exceeds panel dimensions)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "1152x768" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 576x384 54Hz.
(II) SAVAGE(0): Not using default mode "576x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1440x900" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 60Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 60Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 72Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) SAVAGE(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(==) SAVAGE(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x90000000 - 0x97ffffff (0x8000000) MS[B]
	[1] 0	0	0xe0000000 - 0xe007ffff (0x80000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0000100 - 0xf00001ff (0x100) MX[B]
	[7] -1	0	0xf0000000 - 0xf00000ff (0x100) MX[B]
	[8] -1	0	0xf0001000 - 0xf0001fff (0x1000) MX[B]
	[9] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[10] -1	0	0x98000000 - 0x9800ffff (0x10000) MX[B](B)
	[11] -1	0	0x90000000 - 0x97ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e300 - 0x0000e3ff (0x100) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[21] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[22] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[23] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 15296 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 16384 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) SAVAGE(0): [drm] loaded kernel module for "savage" driver
(II) SAVAGE(0): [drm] DRM interface version 1.3
(II) SAVAGE(0): [drm] created "savage" driver at busid "pci:0000:01:00.0"
(II) SAVAGE(0): [drm] added 8192 byte SAREA at 0xefe79000
(II) SAVAGE(0): [drm] mapped SAREA 0xefe79000 to 0xb7c4b000
(II) SAVAGE(0): [drm] framebuffer handle = 0x90000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3156; Card 0x5333/0x8d04]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] command DMA handle = 0xa0000000
(II) SAVAGE(0): [agp] agpTextures handle = 0xa0100000
(II) SAVAGE(0): [drm] aperture handle = 0x92000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x22ec0000
(II) SAVAGE(0): [drm] Status page mapped at 0xb7c4a000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:1572864 
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864 
(II) SAVAGE(0): videoRambytes:0x01000000 
(II) SAVAGE(0): textureSize:0x0095f000 
(II) SAVAGE(0): textureSize:0x0095f000 
(II) SAVAGE(0): textureOffset:0x00680000 
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 9596 kb for textures at offset 0x680000
(II) SAVAGE(0): Using 1023 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		28 128x128 slots
		7 256x256 slots
(==) SAVAGE(0): Backing store disabled
(**) Option "dpms"
(**) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]	reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]	reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]	chipset:0x00000000
(II) SAVAGE(0): [junkers]	sgram:0x00000000
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	frontPitch:0x00000800
(II) SAVAGE(0): [junkers]	backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	backOffset:0x00380000
(II) SAVAGE(0): [junkers]	backPitch:0x00000800
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	depthOffset:0x00500000
(II) SAVAGE(0): [junkers]	depthPitch:0x00000800
(II) SAVAGE(0): [junkers]	textureOffset:0x00680000
(II) SAVAGE(0): [junkers]	textureSize:0x0095f000
(II) SAVAGE(0): [junkers]	textureSize:0x0095f000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	agp:handle:0x00000001
(II) SAVAGE(0): [junkers]	agp:offset:0x01000000
(II) SAVAGE(0): [junkers]	agp:size:0x01000000
(II) SAVAGE(0): [junkers]	agp:map:0x00000000
(II) SAVAGE(0): [junkers]	registers:handle:0xe0000000
(II) SAVAGE(0): [junkers]	registers:offset:0x00000000
(II) SAVAGE(0): [junkers]	registers:size:0x00080000
(II) SAVAGE(0): [junkers]	registers:map:0x00000000
(II) SAVAGE(0): [junkers]	status:handle:0x22ec0000
(II) SAVAGE(0): [junkers]	status:offset:0x00000000
(II) SAVAGE(0): [junkers]	status:size:0x00001000
(II) SAVAGE(0): [junkers]	status:map:0xb7c4a000
(II) SAVAGE(0): [junkers]	agpTextures:handle:0xa0100000
(II) SAVAGE(0): [junkers]	agpTextures:offset:0x00100000
(II) SAVAGE(0): [junkers]	agpTextures:size:0x00f00000
(II) SAVAGE(0): [junkers]	apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:handle:0xa0000000
(II) SAVAGE(0): [junkers]	cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]	cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]	chipset:0x00000006
(II) SAVAGE(0): [junkers]	width:0x00000400
(II) SAVAGE(0): [junkers]	height:0x00000300
(II) SAVAGE(0): [junkers]	mem:0x01000000
(II) SAVAGE(0): [junkers]	cpp:2
(II) SAVAGE(0): [junkers]	zpp:2
(II) SAVAGE(0): [junkers]	agpMode:1
(II) SAVAGE(0): [junkers]	bufferSize:65536
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	backOffset:0x00380000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]	depthOffset:0x00500000
(II) SAVAGE(0): [junkers]	textureOffset:0x00680000
(II) SAVAGE(0): [junkers]	textureSize:0x00900000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers]	agpTextureHandle:0xa0100000
(II) SAVAGE(0): [junkers]	agpTextureSize:0x00f00000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers]	apertureHandle:0x92000000
(II) SAVAGE(0): [junkers]	apertureSize:0x05000000
(II) SAVAGE(0): [junkers]	aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]	statusHandle:0x22ec0000
(II) SAVAGE(0): [junkers]	statusSize:0x00001000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 16 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


does anybody have any idea what could be going on?  it seems to be a common problem from what I have found on the net, but nobody seems to have the solution posted anywhere.....must say...disappointed in the lastest ubuntu

---

### Post by usergentoo on 2007-06-15
I also have the same problem and same error in xorg log. Ive had no luck on fixing it.

---

### Post by nine01a on 2007-06-18
Here's the relevant output of my Xorg log:

```
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
```

I noticed yours is set to /dev/psaux, which I'd think would work but you should try an event node.

If I were in your situation, I'd create a persistent /dev/input entry for your touchpad using udev.

Also, does the touchpad work at all? If not, could it be from a fn+<f-key> lock/unlock feature? That happened to me once.

---

