---
title: "ATI driver installation failure"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Odysseas.nemo on 2006-11-14
Hello all, this is my first post in the forums. I spend the last weeks trying to install the driver for my ATI. I have a clevo 400A notebook, the card is an X700 with 256MB of dedicated memory. During the last weeks I tried everything I could find for installing the driver.

-Installing the restricted modules

-Making a distribution package

-Recompiling the kernel and making the modules

Nothing of all the above worked ](*,). I searched the forums many times with no good results. I am getting desperate with these if have anything to sugest I am ready to try it!

The kernel is (using uname -r)
2.6.15-27-686

Next i placed the /var/log/Xorg.0.log

[PHP]X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux dedalus 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 13 22:59:57 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)

(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,11), BCTRL: 0x0008 (VGA_EN is set)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.30.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), FireMV 2400 (RV380 3151),
	MOBILITY RADEON X300 (M22 3152), MOBILITY FireGL V3200 (M24 3154),
	RADEON X800 (R420 4A48), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E), RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 Series (RV505 715F), RADEON X1600 Series (RV515 7140),
	RADEON X1300 Series (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 Series (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 Series (RV515 714D), RADEON X1300 Series (RV515 714E),
	FireGL V3300 (RV515 7152), RADEON X1300 Series (RV515 715E),
	RADEON X1300 (RV516 7180), RADEON X1600 Series (RV516 7181),
	RADEON X1300 (RV516 7183), MOBILITY RADEON X1450 (M64P 7186),
	RADEON X1300 (RV516 7187), MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1650 Series (RV530 XT2 71C6),
	RADEON X1300 Series (RV530 PRO2 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON Xpress 1200 (RS600 7941),
	RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.30.3
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.30g1                           
(II) ATI Proprietary Linux Driver Build Date: Oct 26 2006 08:05:10
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.30.1.1.2.3-driver-lnx-x86-x86_64-302518
(--) Assigning device section with no busID to primary device
(--) Chipset MOBILITY RADEON X700 (M26 5653) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[5] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[6] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[7] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[8] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[9] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[11] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[16] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[17] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[20] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[21] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[22] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81dbae0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[5] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[6] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[7] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[8] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[9] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[11] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[19] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[21] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[22] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[23] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[24] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[25] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[26] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[31] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B]
	[32] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON X700 (M26 5653)" (Chipset = 0x5653)
(--) fglrx(0): (PciSubVendor = 0x1558, PciSubDevice = 0x04a0)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M26-P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1400  h_sync: 1424  h_sync_end 1480 h_blank_end 1544 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1056 v_blanking: 1066 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 15 modes found for primary display.
(--) fglrx(0): Virtual size is 1400x1050 (pitch 0)
(**) fglrx(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  108.00  1400 1424 1480 1544  1050 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1304 1360 1544  1024 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1176 1232 1544  864 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  108.00  1024 1048 1104 1544  768 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"  108.00  1024 1048 1104 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "848x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  108.00  848 872 928 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  108.00  800 824 880 1544  600 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "720x576": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  108.00  720 744 800 1544  576 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  108.00  720 744 800 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  108.00  640 664 720 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  108.00  640 664 720 1544  400 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  108.00  512 536 592 1544  384 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  108.00  400 424 480 1544  300 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  108.00  320 344 400 1544  240 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  108.00  320 344 400 1544  200 1053 1056 1066 +hsync +vsync
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (88, 88)
(--) fglrx(0): Virtual size is 1400x1050 (pitch 1408)
(**) fglrx(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  108.00  1400 1424 1480 1544  1050 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1304 1360 1544  1024 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1176 1232 1544  864 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  108.00  1024 1048 1104 1544  768 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"  108.00  1024 1048 1104 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "848x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  108.00  848 872 928 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  108.00  800 824 880 1544  600 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "720x576": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  108.00  720 744 800 1544  576 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  108.00  720 744 800 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  108.00  640 664 720 1544  480 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  108.00  640 664 720 1544  400 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  108.00  512 536 592 1544  384 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  108.00  400 424 480 1544  300 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  108.00  320 344 400 1544  240 1053 1056 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 69.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  108.00  320 344 400 1544  200 1053 1056 1066 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.30.3
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc8005000 - 0xc8005fff (0x1000) MX[B]
	[7] -1	0	0xc8000000 - 0xc8003fff (0x4000) MX[B]
	[8] -1	0	0xc8004000 - 0xc80047ff (0x800) MX[B]
	[9] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[10] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[11] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[13] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x0000403f (0x40) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[23] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x00001874 - 0x00001877 (0x4) IX[B]
	[26] -1	0	0x00001890 - 0x00001897 (0x8) IX[B]
	[27] -1	0	0x00001898 - 0x0000189b (0x4) IX[B]
	[28] -1	0	0x000018a0 - 0x000018a7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[34] 0	0	0xc01203b0 - 0xc01203bb (0xc) IS[B](OprU)
	[35] 0	0	0xc01203c0 - 0xc01203df (0x20) IS[B](OprU)
(II) fglrx(0): UMM Bus area: 0xd07ad000 (size=0x07833000)
(II) fglrx(0): UMM area:     0xd07ad000 (size=0x07833000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x07fe0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
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
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1408 x 7138
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us,gr"
(**) Generic Keyboard: XkbLayout: "us,gr"
(**) Option "XkbOptions" "grp:alt_shift_toggle"
(**) Generic Keyboard: XkbOptions: "grp:alt_shift_toggle"
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory[/PHP]

---

### Post by William the Conquerer on 2006-11-14
well, just reading this very quickly it's first off obvious that you're using fglrx.  Are you using dapper still?  You may want to upgrade to edgy if that's feasible, possibly even do a clean install.  I am currently running fglrx right now on my thinkpad and the driver works fine for me.  I followed [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually") again, this was in edgy, not dapper

oh, and looking at your Xorg.0.log file BRIEFLY it looks like the fglrx kernel module is NOT loading...  and I think that's where your whole problem is.  If you type ```
$ sudo modprobe fglrx
``` in a terminal it will probably give you an error and say it can't load it, that error may be important for troubleshooting.  Oh, and after modprobing, ```
$ dmesg |grep fglrx
``` in a terminal might give you some more helpful hints

---

### Post by Odysseas.nemo on 2006-11-15
I am using dapper because I am not feeling easy with upgrading. 
You are right the modprobe gave an error 

"FATAL: Could not open '/lib/modules/2.6.15-27-686/volatile/fglrx.ko': No such file or directory"

the dmesg didnt return anything. 

I read the post and the procedure is the same as in dapper and in dapper it gave me no results :(

---

