---
title: "Ubuntu 5.04 and fresh ATi driver"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by mobal on 2005-07-27
hello!

I have installed the fresh ati driver. A configured and works fine but when im log out my x server crashes. i have installed the ati driver three times with three ways but the accomplishment is the same. please help because i want 3d in my ubuntu. thaks! kernel: 2.6.10 but i tried with debian 3.1 sarge and the same problem.

(sorry for the english but my first language is hungarian.)

---

### Post by mobal on 2005-07-28
please help! im very nervous  ](*,)

---

### Post by mamato on 2005-07-28
As far as I know, there are fglrx driver for xorg, named xorg-driver-fglrx or something like that.. 
All you have to do is "apt-get install" that package..
If you can't find the package, maybe you have to add the universe, multiverse and restricted to your repository...
Hope that's help..

---

### Post by pailhead on 2005-07-28
[QUOTE=mamato]As far as I know, there are fglrx driver for xorg, named xorg-driver-fglrx or something like that.. 
All you have to do is "apt-get install" that package..
If you can't find the package, maybe you have to add the universe, multiverse and restricted to your repository...
Hope that's help..[/QUOTE]
 Yah I did that command there but when I went to fglrx in xorg.conf I rebooted and all I got was a black screen. No desktop.  3D seems very flakey currently...

---

### Post by mobal on 2005-07-28
[QUOTE=mamato]As far as I know, there are fglrx driver for xorg, named xorg-driver-fglrx or something like that.. 
All you have to do is "apt-get install" that package..
If you can't find the package, maybe you have to add the universe, multiverse and restricted to your repository...
Hope that's help..[/QUOTE]

not works. when i logout the xserver freezes

---

### Post by abrouwers on 2005-07-28
Well, even though the driver in the repos is a version or two old, it actually works quite well with the kernel.  If you've already apt-get install xorg-driver-fglrx, then you might have the module running...try:

sudo lsmod | grep fglrx

If not, use apt to install (as mentioned above). 

Now, the problem seems to be with your xorg.conf; try running: 

sudo fglrxconfig

and create a new one based off of fglrx.  Then, restart X, and you should be good to go :)

---

### Post by mobal on 2005-07-28
not works. in glxgears i have only 100-200 fps.

---

### Post by mobal on 2005-07-28
root@ubuntu:~ # glxgears
610 frames in 8.0 seconds = 76.250 FPS
151 frames in 7.0 seconds = 21.571 FPS
339 frames in 5.0 seconds = 67.800 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


what is it? x connection... ?

---

### Post by mamato on 2005-07-29
can you give us the content of **/var/log/Xorg.0.log** ? maybe it can help to solve your problem..

---

### Post by jimchristopher on 2005-12-27
I have this crashed x server problem as well.  when i logout, it just dumps me to a black screen, no login no nothing.  I am using a Shuttle SN25P and an ATI X800XL with the fglrx driver loaded.  here is my /var/log/xorg.0.log.. it was to big to attach so ive posted chunks


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Thu Dec 22 11:37:10 U

OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 27 00:17:01 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "BenQ FP931-D"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(W
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
(II) PCI: 00:00:0: chip 10de,005e card 1297,5036 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1297,5036 rev a3 class 06,01,00 hdr 80

(II) PCI: 01:00:0: chip 1002,554d card 1002,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,556d card 1002,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: 05:06:0: chip 1412,1724 card 1297,5036 rev 01 class 04,01,00 hdr 00
(II) PCI: 05:07:0: chip 1106,3044 card 1106,3044 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0206 (VGA_EN is cleared)

(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x554d) rev 0, Mem @ 0xb0000000/28, 0xc0030000/16, I/O @ 0x9000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x556d) rev 0, Mem @ 0xc0020000/16
SNIPPED TO SHORTEN
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
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

(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
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
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
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
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON X800 XL (R430 554D) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[6] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[7] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[8] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[9] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[10] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[11] -1	0	0xc0030000 - 0xc003ffff (0x10000) MX[B](B)
	[12] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xc0020000 - 0xc002ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8210658
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0000000 - 0xd00007ff (0x800) MX[B]
	[6] -1	0	0xd0100000 - 0xd0100fff (0x1000) MX[B]
	[7] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[8] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[9] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[10] -1	0	0xd0104000 - 0xd0104fff (0x1000) MX[B]
	[11] -1	0	0xc0030000 - 0xc003ffff (0x10000) MX[B](B)
	[12] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xc0020000 - 0xc002ffff (0x10000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[25] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[26] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[27] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X800 XL (R430 554D)" (Chipset = 0x554d)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0302)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xb0000000
(--) fglrx(0): MMIO registers at 0xc0030000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.7
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2003, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: R430
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) fglrx(0): Connected Display1: DFP on internal TMDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: BNQ  Model: 7675  Serial#: 2936
(II) fglrx(0): Year: 2004  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.614
(II) fglrx(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz

(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: BenQ FP931-D
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 31 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz

, 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x00000801
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0030000 - 0xc003ffff (0x10000) MX[B]
	]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xb0701000 (size=0x078ef000)
(II) fglrx(0): UMM area:     0xb0701000 (size=0x078ef000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
ALL THE WAY TO 
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8ddb000
(II) fglrx(0): [drm] mapped SAREA 0xf8ddb000 to 0xb7b04000
(II) fglrx(0): [drm] framebuffer handle = 0xb0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xc0030000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0xf8f84000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xb0000000 FBMappedSize: 0x00701000
(II) fglrx(0): Splitting WC range: base: 0xb0000000, size: 0x701000
(II) fglrx(0): Splitting WC range: base: 0xb0400000, size: 0x301000
(II) fglrx(0): Splitting WC range: base: 0xb0600000, size: 0x101000
(==) fglrx(0): Write-combining range (0xb0700000,0x1000)
(==) fglrx(0): Write-combining range (0xb0600000,0x101000)
(==) fglrx(0): Write-combining range (0xb0400000,0x301000)
(==) fglrx(0): Write-combining range (0xb0000000,0x701000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
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
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
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
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
SetClientVersion: 0 9

---

### Post by jimchristopher on 2005-12-31
using an nv 6600GT makes this problem go away!

---

