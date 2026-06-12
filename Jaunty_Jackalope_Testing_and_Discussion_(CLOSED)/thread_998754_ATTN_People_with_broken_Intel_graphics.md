---
title: "ATTN: People with broken Intel graphics"
date: 2008-12-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klange on 2008-12-01
Alright, since people don't seem to read bug reports, even when they find them and comment on them, I'll just go right out there and post it:

**e**: In order to keep the number of threads low, I'm going to expand this for general discussion of any Intel issues.

**Issue #1: There is an unmarked dependency on the package *libdrm-intel1*:**
The recent upgrade to version 2.5.1 of the Intel display drivers has an *unmarked dependency* on the package [FONT="monospace"]`libdrm-intel1`[/FONT]. Without it, X will crash because the Intel driver will fail to initialize.

_Solution:_
```
sudo apt-get install libdrm-intel1
```

The bug report is [#303177](https://bugs.launchpad.net/bugs/303177). It has not yet been fixed.

**e**: Sorry! Transposed the `l` and the `1`, it should be libdrm-intel1, not libdrm-inte1l. Maybe I shouldn't post public service announcements at 6AM.

**Issue #2: "(EE) intel(0): Failed to pin front buffer: cannot allocate memory.":**
After installing libdrm-intel1, some users are reporting general issues with the driver involving the error message above. I'm not having these problems, but I'd say the drivers themselves are to blame.

_Solution:_
*No solution is currently known for this issue.*
RAOF thinks it's just some bug in libdrm.
**e**: Has this been resolved? Have a solution? Share it!

**Issue #3: Software Rasterizer**
This occurs when the DRI device blocks aren't set with the right permissions. It's a bug in X that ignores the "DRI" permission option.
The fix:
```
sudo chmod a+rw /dev/dri/*
```
(Use the * in case you have multiple device instances, which you probably won't but better safe than sorry)
You may need to do this every time you start X. Hopefully this bug will be resolved.

**Issue #4: Recent updates break X**
Though I've gotten my server to start with the Intel drivers, starting Compiz kills it (but running glxgears did not). This problem seems to be effecting all Intel cards, so it's a general driver issue.

---

### Post by DougieFresh4U on 2008-12-01
> **WindowsSucks said:**
> Alright, since people don't seem to read bug reports, even when they find them and comment on them, I'll just go right out there and post it:

The recent upgrade to version 2.5.1 of the Intel display drivers has an *unmarked dependency* on the package [FONT="monospace"]`libdrm-intel1`[/FONT].

If your Intel graphics are broken (ie, X does not start, or starts in low-graphics mode, or uses the vesa driver), install this package:

```
sudo apt-get install libdrm-inte1l
```

The bug report is [#303177](https://bugs.launchpad.net/bugs/303177). It has not yet been fixed.

Thanks for your suggestion, but I get this:
```
dougie@DougiesLeanMachine:~$ sudo apt-get install libdrm-inte1l
[sudo] password for dougie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdrm-inte1l

```
Synaptic has 'libdrm-intel**1**' listed. Would that be what you are refering to?

---

### Post by vishalrao on 2008-12-01
looks like you swapped the L and the ONE letters :D  -intel1 not -inte1l

edit: oh its swapped in the OP's code section

---

### Post by shirishagarwal on 2008-12-01
What Dougie just needed to do is do sudo apt-get install libdrm-in(and use tab-completion) :)

---

### Post by shirishagarwal on 2008-12-01
This is the output from my /var/log/Xorg.9.log after installing libdrm-intel1. Still no love as far as GUI is concerned. 

```

X.Org X Server 1.5.3
Release Date: 5 November 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Mugglewille-desktop 2.6.28-1-ub-generic #1 SMP Wed Nov 26 19:15:48 UTC 2008 i686
Build Date: 27 November 2008  09:36:01AM
xorg-server 2:1.5.3-1ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  1 18:24:14 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xd0000000/0, 0xdff80000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
	compiled for 1.5.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.3, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 2.5.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile IntelÂ® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xDFF80000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 1 display pipe available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"

(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"

(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"

(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"

(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"

(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "PHL", prod id 13
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x350"x0.0   25.18  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 -hsync +vsync (50.9 kHz)
(II) intel(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "PHL", prod id 13
(II) intel(0): Output VGA connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA using initial mode 1280x960
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (310, 230) mm
(**) intel(0): DPI set to (131, 176)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.3, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 240640 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 962556 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xdff80000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 39321600 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x03a7f000 (pgoffset 14975)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x03a80000 (pgoffset 14976)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x06000000 (pgoffset 24576)
(EE) intel(0): Failed to pin front buffer: Cannot allocate memory

Fatal server error:
Couldn't bind memory for BO front buffer

(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2

```

Somebody said this is an alternative way to do the same but haven't tried it as yet. This one is without installing libdrm though. 

```
sudo su
cd /usr/lib
ln -s libdrm.so.2.31 libdrm_intel.so.1
sudo killall gdm
gdm 
```

If anybody is able to get working GUI from the latter please lemme know.

---

### Post by klange on 2008-12-01
Oops, transposed the l and the 1, sorry about that. Fixed in OP.

@shirishagarwal: Your issue is due to a different bug (but you need the library anyway if you want any hope of getting it to work).

---

### Post by DougieFresh4U on 2008-12-01
Well, I followed OP instructions and rebooted. The following message appears in a little gray box:

[B]```
Ubuntu is running in low graphics mode. The following error was encountered.You may need to update your configuration to solve this:
(EE) intel(0): Failed to pin front buffer: cannot allocate memory.
```[/B]

Could some one please explain to me what that is all about and a solution to solve it. Still stuck on that 'vesa'
Thanks

---

### Post by shirishagarwal on 2008-12-01
> **WindowsSucks said:**
> 

@shirishagarwal: Your issue is due to a different bug (but you need the library anyway if you want any hope of getting it to work).

What bug is that, if you have posted the bug please lemme know would subscribe to the same. If not, please lemme know what is needed to be done. 

Also, just checked the changelog of libdrm on launchpad. 

[https://launchpad.net/ubuntu/+source/libdrm](https://launchpad.net/ubuntu/+source/libdrm)

```


2.4.1-0ubuntu6
Published in jaunty-release on 2008-11-27

libdrm (2.4.1-0ubuntu6) jaunty; urgency=low

  * libdrm-intel1 Replaces libdrm2 (<= 2.4.1-0ubuntu5)

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Thu, 27 Nov 2008 10:25:29 +0200

Available diffs

    * 2.4.1-0ubuntu5 to 2.4.1-0ubuntu6 (500 bytes)

2.4.1-0ubuntu5
Superseded in jaunty-release on 2008-11-27

libdrm (2.4.1-0ubuntu5) jaunty; urgency=low

  * Split the symbols file (libdrm2, libdrm-intel1), remove shlibs and
    use dh_makeshlibs properly instead.

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Thu, 27 Nov 2008 09:42:59 +0200

Available diffs

    * 2.4.1-0ubuntu4 to 2.4.1-0ubuntu5 (1014 bytes)

2.4.1-0ubuntu4
Superseded in jaunty-release on 2008-11-27

libdrm (2.4.1-0ubuntu4) jaunty; urgency=low

  * debian/libdrm2.install: Careful with those wildmarks.
    libdrm2 got libdrm_intel.so too, don't do that.

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Thu, 27 Nov 2008 08:58:47 +0200

Available diffs

    * 2.4.1-0ubuntu3 to 2.4.1-0ubuntu4 (365 bytes)

2.4.1-0ubuntu3
Superseded in jaunty-release on 2008-11-27

libdrm (2.4.1-0ubuntu3) jaunty; urgency=low

  * Actually build the new libdrm-intel1 package.

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Wed, 26 Nov 2008 14:41:08 +0200

Available diffs

    * 2.4.1-0ubuntu2 to 2.4.1-0ubuntu3 (1.0 KiB)

2.4.1-0ubuntu2
Superseded in jaunty-release on 2008-11-26

libdrm (2.4.1-0ubuntu2) jaunty; urgency=low

  * Build-depend on libpthread-stubs0-dev and pkg-config (FTBFS).
  * Make libdrm-dev depend on libdrm-intel1.

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Wed, 26 Nov 2008 01:15:07 +0200

Available diffs

    * 2.4.1-0ubuntu1 to 2.4.1-0ubuntu2 (8.1 KiB)

2.4.1-0ubuntu1
Superseded in jaunty-release on 2008-11-26

libdrm (2.4.1-0ubuntu1) jaunty; urgency=low

  * New upstream release.


Available diffs

    * 2.3.1-2 to 2.4.1-0ubuntu1 (124.7 KiB)

2.3.1-2
Superseded in jaunty-release on 2008-11-26

libdrm (2.3.1-2) unstable; urgency=high

  * Remove from the source package a bunch of files that are only used by the
    kernel drm component.  This gets rid of the mga, r128 and radeon
    microcode, and thus closes: #502675.  Thanks, Ben Hutchings!


Available diffs

    * 2.3.1-0build1 to 2.3.1-2 (327.6 KiB)

2.3.1-0build1
Superseded in jaunty-release on 2008-11-05
Published in intrepid-release on 2008-07-03

libdrm (2.3.1-0build1) intrepid; urgency=low

  * New upstream release, needed for mesa 7.1 & xorg-server 1.5.

 -- Timo Aaltonen < tepsipakki@ubuntu.com>   Thu, 03 Jul 2008 16:43:22 +0300

Available diffs

    * 2.3.0-4ubuntu1 to 2.3.1-0build1 (731.9 KiB)

```

What interesting I found out in the above is first the split of libdrm2 and libdrm-intel1 and then replacing libdrm2 with libdrm-intel1 entirely. Also found another bug [lpbug]303567[/lpbug] which I guess is at giving more documentation in the changelog and any release notes. 

Any update to mesa or the intel driver or libdrm please put in the thread as well. 

Looking forward to getting GUI back :)

---

### Post by RAOF on 2008-12-01
> **shirishagarwal said:**
> ...
```
sudo su

cd /usr/lib
ln -s libdrm.so.2.31 libdrm_intel.so.1
sudo killall gdm
gdm 
```

If anybody is able to get working GUI from the latter please lemme know.
Eeep!  What makes you think this will lead to anything but madness? :)


> **DougieFresh4U said:**
> Well, I followed OP instructions and rebooted. The following message appears in a little gray box:

[B]```
Ubuntu is running in low graphics mode. The following error was encountered.You may need to update your configuration to solve this:
(EE) intel(0): Failed to pin front buffer: cannot allocate memory.
```[/B]

Could some one please explain to me what that is all about and a solution to solve it. Still stuck on that 'vesa'
Thanks

I suspect (but haven't done any checking) this is at least in part due to the [messed-up libdrm](https://bugs.edge.launchpad.net/ubuntu/+source/libdrm/+bug/303567).  The solution there would be to wait until libdrm is fixed, and everything is rebuilt against the fixed libdrm.

---

### Post by jerrylamos on 2008-12-01
IBM Thinkpad R31 with Intel graphics got flickering black screen and no keyboard response with the recent update.

sudo apt-get install libdrm-intel1

gets my background and a white banner at top and bottom of the screen with no applets at all, keyboard dead.  sudo apt-get install ubuntu-desktop ran quite a while, after it completed no help at all.

Jerry

---

### Post by Martym on 2008-12-02
OK so I rebooted tonight and received the dreaded "Ubuntu is running in low graphics mode."  I typed sudo apt-get install libdrm-intel1 and hit the GO button.

All I get for my troubles is "Couldn't find package libdrm-intel1"

apt-get and aptitude seem to be working fine.  What do I have to do to install this package?

---

### Post by DougieFresh4U on 2008-12-02
> **jerrylamos said:**
> IBM Thinkpad R31 with Intel graphics got flickering black screen and no keyboard response with the recent update.

sudo apt-get install libdrm-intel1

gets my background and a white banner at top and bottom of the screen with no applets at all, keyboard dead.  sudo apt-get install ubuntu-desktop ran quite a while, after it completed no help at all.

Jerry
Sorry to hear your misfortune. I at least have a working desktop and have rebooted with out much 'bitchin from machine. I am stuck using 'vesa' until this Intel issue is resolved. I was stuck with 'vesa' through out Intrepid as well.

---

### Post by DougieFresh4U on 2008-12-02
> **Martym said:**
> OK so I rebooted tonight and received the dreaded "Ubuntu is running in low graphics mode."  I typed sudo apt-get install libdrm-intel1 and hit the GO button.

All I get for my troubles is "Couldn't find package libdrm-intel1"

apt-get and aptitude seem to be working fine.  What do I have to do to install this package?

I installed it after finding it in Synaptic. Do you see it in Synaptic?

---

### Post by anhvu2875 on 2008-12-02
i also installed that and still got ''Ubuntu in low-graphics mode'' always so have to back to Intrepid -> so sad !! :(:(

---

### Post by Martym on 2008-12-02
> **DougieFresh4U said:**
> I installed it after finding it in Synaptic. Do you see it in Synaptic?

I cannot even get into my desktop to see Synaptic :sad:  I have, for all intents and purposes, the equivalent of a very expensive 5150 terminal

---

### Post by DougieFresh4U on 2008-12-02
> **Martym said:**
> I cannot even get into my desktop to see Synaptic :sad:  I have, for all intents and purposes, the equivalent of a very expensive 5150 terminal

Sorry to hear that.I am no 'guru', so can not help much. Have you tried installing it via terminal?
Also, once I got it installed, it still wasn't working properly. Still getting 'low graphics mode'. Just waiting for more updates that can hopefully fix.

---

### Post by shirishagarwal on 2008-12-02
what I don't know how you guys are the 'low graphics mode' . I'm not even there.

---

### Post by DougieFresh4U on 2008-12-02
> **shirishagarwal said:**
> what I don't know how you guys are the 'low graphics mode' . I'm not even there.

Each and every time I boot, this is what appears just before login screen, and I just 'ok' my way through it as the 'fix graphics' option doen't work.

[B]Ubuntu is running in low graphics mode. The following error was encountered.You may need to update your configuration to solve this:
(EE) intel(0): Failed to pin front buffer: cannot allocate memory.[/B]

---

### Post by Martym on 2008-12-02
Well, since I am not using jaunty, and I wanted this fixed today, I just reinstalled.  A few minutes reading my notes and several commands later and I am back up and running where I left off.

Looking through Synaptic there is no libdrm-intel1 in Hardy *shrug*

Oh well, I guess it really does pay to read the headings when clicking on a search item.


Thanks for your assistance everyone.

---

### Post by DougieFresh4U on 2008-12-02
Just had a few updates and a couple of them were for intel. Don't know if they are the ones to fix the problem as I am leery of rebooting to find out (chicken sh*t)
[HTML]Setting up xserver-xorg-video-intel (2:2.5.1-1ubuntu2) ...

Setting up xserver-xorg-video-intel-dbg (2:2.5.1-1ubuntu2) ...
Setting up gnome-settings-daemon (2.25.2-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/gnome-settings-daemon.desktop ...

Setting up gnome-settings-daemon-dev (2.25.2-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dougie@DougiesLeanMachine:~$ sudo apt-get -f install
[/HTML]

---

### Post by shirishagarwal on 2008-12-02
There's another that's just been built of intel driver 2:2.5.1-1ubuntu4, will wait for the kernel to be built and then install both the new driver as well as the new kernel as well.

[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.5.1-1ubuntu4/+build/803084](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.5.1-1ubuntu4/+build/803084)

This is the changelog of the latest releases done today itself. 

```



xserver-xorg-video-intel (2:2.5.1-1ubuntu4) jaunty; urgency=low

  * Drop 111_textured_video_option.patch.  XvPreferOverlay (commit
    24c34f02) now provides an equivalent capability for turning textured
    video off, making this patch redundant.

 -- Bryce Harrington < bryce@ubuntu.com>   Tue, 02 Dec 2008 12:47:10 -0800

   
2:2.5.1-1ubuntu3
Published in jaunty-release 56 minutes ago

xserver-xorg-video-intel (2:2.5.1-1ubuntu3) jaunty; urgency=low

  * 102_quirk_hp_2730p.patch: pipea quirk for hp 2730p (LP: #291555)

 -- Bryce Harrington < bryce@ubuntu.com>   Tue, 02 Dec 2008 11:47:28 -0800

2:2.5.1-1ubuntu2
Superseded in jaunty-release 55 minutes ago

xserver-xorg-video-intel (2:2.5.1-1ubuntu2) jaunty; urgency=low

  * Drop 128_stolen_memory_counting_g4x.patch (already upstream)
  * Refresh and re-enable 111_textured_video_option.patch

 -- Bryce Harrington < bryce@ubuntu.com>   Tue, 02 Dec 2008 09:13:34 -0800

2:2.5.1-1ubuntu1
Superseded in jaunty-release 2 hours ago

xserver-xorg-video-intel (2:2.5.1-1ubuntu1) jaunty; urgency=low

  * Merge with debian experimental.  Remaining changes:
    - debian/control:
      + Change the maintainer address.
      + Add lpia to the list of architectures.
      + Drop Vcs-* as we're not using these repos for -intel.
    - debian/patches:
      + Renumber Ubuntu patches +100
      + 101_quirk_quanta_w251u.patch
      + 111_textured_video_option.patch
      + 128_stolen_memory_counting_g4x.patch
  * Drop 01_fix_compiz_video.diff.  Was already disabled in Ubuntu previously
  * Drop 05_intel_exa_force_greedy.patch.  Should no longer be necessary.
  * Drop patches already upstream:
    - 20_thinkpad_g40_quirk.patch
    - 21_quirk_lenovo.patch
    - 22_no_pipe_for_hotplug_detection.patch
    - 23_quirks_studiohybrid_eeepc_and_w251u.patch
    - 24_no_render_suspend
    - 25_quirk_nc6110.patch
    - 26_i830-use-lfp-data-ptrs.patch
    - 27_disable_fbc_on_965.patch


```

I just took the liberty of not listing the available diff with each release.

---

### Post by anhvu2875 on 2008-12-02
any good news ? i was still using Intrepid ! :(:(

---

### Post by Melk79 on 2008-12-02
I ran into "broken intel" graphics while installing Intrepid Ibex on an older Dell Dimension 4500s with Intel Integrated Graphics Card.  The Live CD (and Alternate CD) couldn't load X properly and only safe graphics mode would work.  After a full install the video was still stuck with the 'vesa' driver in safe graphics mode (poor resolution & 4:3 ratio) despite having the proper intel packages installed in synaptic.  I installed the libdrm-intel1 package, but to no avail.

After some fooling around I remembered Ubuntu 7.10 loaded properly on this system a while back.  I ran that LiveCD and copied the xorg.conf text to my external hard drive.  Then i booted back into 8.10 regularly and copied the video sections over my very limited video section in xorg.conf.

My copied section is this:
> Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"HB191"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"HB191"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

This is used with a Hanns-G 19" Widescreen HB191 monitor.  Perhaps you could restore your intel video in a similar method by using a LiveCD that configures your screen properly with your hardware setup?

---

### Post by shirishagarwal on 2008-12-02
Melk79, 
 While this is not a Intrepid support thread, I would suggest you try two things. 

First do 

```
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
```

This is so even if we mess up something we have the original to look,understand and use. A sort of backup as well. 

Then using your favorite editor open the menu.lst file. 

```
$ gksudo gedit /boot/grub/menu.lst
```

Go to where the kernels list is at the bottom. It would show something similar like:-

```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		49b2cc28-fa6d-4d0d-ae16-040861151df0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro **xforcevesa** quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		49b2cc28-fa6d-4d0d-ae16-040861151df0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro **xforcevesa**  single
initrd		/initrd.img-2.6.27-7-generic

```

What you want to do is just remove that xforcevesa line so it reads 

```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		49b2cc28-fa6d-4d0d-ae16-040861151df0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		49b2cc28-fa6d-4d0d-ae16-040861151df0
kernel		/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro single
initrd		/initrd.img-2.6.27-7-generic

```

The UUID given to your hard disk would be different so don't worry if that is different. 

In fact in Intrepid you shouldn't need any xorg.conf. I have the same chipset as yours and mine is completely blank. 

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I am able to scale upto 1600*1024 on my old trusty CRT 17" (15" really) monitor.

---

### Post by Starks on 2008-12-02
Somewhat on topic...

xserver-xorg-video-intel - 2:2.4.99.1~git20081129.5f347020-0ubuntu0tormod~hardy
xserver-xorg-video-intel - 2:2.4.97.0+git20081129.5f347020-0ubuntu0tormod

Anyone got either of these working on Jaunty?

---

### Post by shirishagarwal on 2008-12-03
the versions in jaunty is 2:2.5.1-1ubuntu2

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001476.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001476.html)

I don't think there is any gain in going backwards. As given elsewhere the developers and many people the issue is with libdrm and not the driver for the issue in jaunty which was known as libdrm2 in intrepid. 

Info. for libdrm2 

Description: Userspace interface to kernel DRM services -- runtime
 This library implements the userspace interface to the kernel DRM services.  DRM stands for "Direct Rendering
 Manager", which is the kernelspace portion of the "Direct Rendering Infrastructure" (DRI). The DRI is currently
 used on Linux to provide hardware-accelerated OpenGL drivers. 
 
 This package provides the runtime environment for libdrm.

In Jaunty the package has been split in libdrm-intel and another symbol file as given before.

---

### Post by DougieFresh4U on 2008-12-03
Just checked updates and there were 2 Intel updates. Don't know if they are the ones that will fix, but I am not ready to try a reboot just yet. Maybe some one would wanna try and see if it 'breaks' or 'makes' ):P

---

### Post by Starks on 2008-12-03
so... what's the status on gem and dri2?

---

### Post by RAOF on 2008-12-03
> **Starks said:**
> so... what's the status on gem...

Not in our kernel modules.
> **Starks said:**
> ...and dri2?
disabled in our X build.

---

### Post by Starks on 2008-12-03
so...

ubuntu+1 or ubuntu+2?

---

### Post by shirishagarwal on 2008-12-03
There is an updated libdrm, let's see if this one fixes the issue

[https://launchpad.net/ubuntu/+source/libdrm](https://launchpad.net/ubuntu/+source/libdrm)

---

### Post by klange on 2008-12-03
> **RAOF said:**
> Not in our kernel modules.

disabled in our X build.

So that's why I only get 20fps in glxgears...

---

### Post by shirishagarwal on 2008-12-03
Even with the updated libdrm it doesn't seem to be fixed.

There was one bug filed against libdrm 

[lpbug]303177[/lpbug] as well as this one [lpbug]304163[/lpbug] 

I dunno how he got failsafe X.

I did file [lpbug]304871[/lpbug]

---

### Post by Starks on 2008-12-03
> **RAOF said:**
> Not in our kernel modules.

disabled in our X build.

dri2 just landed in the intel video git master, right?

---

### Post by shirishagarwal on 2008-12-03
I had to re-read your first post again, I'm also hit with the 

**Fatal server error: Couldn't bind memory for BO front buffer**

---

### Post by RAOF on 2008-12-03
> **WindowsSucks said:**
> So that's why I only get 20fps in glxgears...

No.  GEM and DRI2 aren't really performance wins[1], at least not immediately[2].  They're *correctness* (and feature) wins - DRI2 finally allows GLX to work with Composite in a non-stupid way.

[1]: Actually, last benchmark I saw on dri-devel, both memory managers (TTM & GEM) entailed substantial performance penalties.  That was a while ago now, though.
[2]: Although IIRC having a memory manager can allow some optimisations that are hard now.

---

### Post by shirishagarwal on 2008-12-04
Still no joy [lpbug]304871[/lpbug]

---

### Post by DougieFresh4U on 2008-12-06
Ok, what is up with this Intel graphics crap. Updates this eve didn't do a thing to help situation at all!!
Also, when booting and getting the 'starting in low graphics mode' messege, what good is the little box that pops up and ask if you would like to 'continue' or 'reconfigure for this hardware'? Because when you select 'reconfigure for this hardware' it does **_absolutely nothing_** and causes me to do a hard shut down.
I guess I am to be lucky to at least boot up to a working desktop and I am using the 2.6.28-2.3 kernel
Sorry for the rant ) (I feel better, for now) ):P

---

### Post by klange on 2008-12-06
> **RAOF said:**
> No.  GEM and DRI2 aren't really performance wins[1], at least not immediately[2].  They're *correctness* (and feature) wins - DRI2 finally allows GLX to work with Composite in a non-stupid way.

[1]: Actually, last benchmark I saw on dri-devel, both memory managers (TTM & GEM) entailed substantial performance penalties.  That was a while ago now, though.
[2]: Although IIRC having a memory manager can allow some optimisations that are hard now.

Heh? While my last post wasn't all that serious, I have to say, GEM was clocked at having significant improvements in texture operations and also increased the speed of standard 3d operations. One of the benchmarks showed a 30% speed improvement overall, and if that's based on 2.4.1 (as that was the norm when I saw the benchmark, and GEM was on a separate branch back then), that means a lot. GEM doesn't just mean DRI2, it means proper handling of graphics memory.

---

### Post by ShirishAg75 on 2008-12-06
I would be just cool if I get a GUI happening without using the vesa or something very very slow. I know it would most probably be all good when its Jaunty releases, a little earlier is always better.

---

### Post by jerrylamos on 2008-12-06
Today's daily build 20081206 boots, runs, installs on integrated Intel Graphis on IBM Thinkpad R31 and IBM ThinkCentre A30.  They both hung big time on loading desktop if using Jaunty from updates.

The Thinkpad 82830 CGC is O.K. as an Alpha (Jaunty sound is dead) the ThinkCentre tower 82845G says it is running Gnome fail-safe (Jaunty sound is dead) You Tube Leona Lewis a little jerky (can't hear her sing of course  Whoops!  If I do Volume Control PCM max she speaks up (pretty scratchy)).

Not about to do any more updates.  I'll download CD Live if they fit on a CD and try that first, and always dual boot so the boot that works can look at logs on the dead one.

Jerry

---

### Post by Jynx97 on 2008-12-07
I got the "Couldn't bind memory for BO front buffer" error after installing the latest intel driver. 

I uninstalled it, and tried several previous drivers. 

Finally xserver-xorg-video-intel_2.4.1 did the trick.

---

### Post by ShirishAg75 on 2008-12-07
Jynx97 perhaps you can subscribe and click on this bug affects me too [lpbug]304871[/lpbug]

---

### Post by ShirishAg75 on 2008-12-08
Hi all, 
 A new metacity is there, please upgrade and see if that fixes the issue or not?

[https://launchpad.net/ubuntu/+source/metacity](https://launchpad.net/ubuntu/+source/metacity)

```

metacity (1:2.25.34-0ubuntu1) jaunty; urgency=low

  * New upstream release
    - Fixes to Thomas's earlier fixes (Matt) (#562939)
    - Fixes to allow building without compositor again (Thomas)
    - Fixes for -Wall problems (Thomas)
    - Various tool updates (Thomas)
  * debian/control.in:
    - Downgrade gnome-doc-tools to 0.8.0

 -- Pedro Fragoso <[[IMG]https://edge.launchpad.net/@@/person[/IMG] ember@ubuntu.com]("https://edge.launchpad.net/%7Eember")>   Thu, 04 Dec 2008 16:27:04 +0000
```

It got built around an hour ago on various architectures.

---

### Post by Jynx97 on 2008-12-08
I upgraded to the new metacity, and still get the same error "Couldn't bind memory for BO front buffer". I have rolled back the intel video driver to 2.4.1, and it is now working.

---

### Post by ShirishAg75 on 2008-12-09
Jynx97, 
 Can you attach your lspci details on the [lpbug] 304871 [/lpbug] . Everybody else who has the same error "[COLOR=Red]Fatal server error: Couldn't bind memory for BO front buffer[/COLOR]" attach their lspci's on the bug as well. Thank you in advance.

---

### Post by ShirishAg75 on 2008-12-09
Hi all, 
 This bug inspired me to put up a blog post about the same [http://flossexperiences.wordpress.com/2008/12/10/legacy-hardware-gnulinux/](http://flossexperiences.wordpress.com/2008/12/10/legacy-hardware-gnulinux/) . The bug got reported upstream [18974]("https://bugs.freedesktop.org/show_bug.cgi?id=18974") and they say that having DRI2 will most likely fix it. So looking for comments from people on the same.

---

### Post by Nathan Sweeney on 2008-12-11
Has this recently been fixed?  I just installed Jaunty on a 10 GB partition to test it out, and my graphics are working the same as in Intrepid.  I have the Intel 4500MHD, compiz works fine and glxgears gives me around 500 fps, same as Intrepid.

---

### Post by anhvu2875 on 2008-12-11
more good news mates ??!

---

### Post by ShirishAg75 on 2008-12-11
just a small update to mesa 7.2 happening 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001700.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001700.html)

* debian/rules (CFLAGS): Avoid recursive reference.

---

### Post by Nathan Sweeney on 2008-12-12
> **Nathan Sweeney said:**
> Has this recently been fixed?  I just installed Jaunty on a 10 GB partition to test it out, and my graphics are working the same as in Intrepid.  I have the Intel 4500MHD, compiz works fine and glxgears gives me around 500 fps, same as Intrepid.

My apologies, I'm afraid I must redact that statement.  I thought I was getting 500 FPS on Intrepid, but I went back to make sure...

Intrepid 2.6.27-9 Kernel
790 FPS with the CPU freq set to "On Demand" from the Gnome applet (applet stated 800 MHz)
1010 FPS with the CPU freq set to 2.0 GHz (T5800 C2D 2.0 GHz Proc)

Jaunty 2.6.27-7 after latest updates
All over the place with CPU Freq at on demand (190-300 FPS)
290 FPS with CPU Freq at 2.0 GHz

Jaunty 2.6.28-2
similar results to 2.6.27-7 Jaunty

---

### Post by ihavenoname on 2008-12-13
> **Nathan Sweeney said:**
> My apologies, I'm afraid I must redact that statement.  I thought I was getting 500 FPS on Intrepid, but I went back to make sure...

Intrepid 2.6.27-9 Kernel
790 FPS with the CPU freq set to "On Demand" from the Gnome applet (applet stated 800 MHz)
1010 FPS with the CPU freq set to 2.0 GHz (T5800 C2D 2.0 GHz Proc)

Jaunty 2.6.27-7 after latest updates
All over the place with CPU Freq at on demand (190-300 FPS)
290 FPS with CPU Freq at 2.0 GHz

Jaunty 2.6.28-2
similar results to 2.6.27-7 Jaunty


What are the developers saying with reguard to this? Fedora has this problem right now with it's current stable release, I certainly hope Ubuntu won't release with this issue.

update:
for me compiz seemingly works fine (I am getting around 700+ fps on glxgears w/compiz running. But moving large windows around leads to choppy performance (my window is about 1 seconds behind my mouse when I move it, resizing isn't a big issue). Resizing the same large window and making it much smaller (for example nautilus to gcalc size) it moves at a normal speed. Disable wobbly windows (moving from extra to normal under the last tab in the Apperance utility) brings speed to an acceptable rate, though at times it does seem to lag a bit.  

This is the issue that I am reffering to above. There is a bug report on this no?

---

### Post by thread on 2009-01-19
My issue doesn't seem to be related to the ones the OP fixes, but it's a new issue that seems to be cropping up in a few threads. At a glance:

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.3-devel
```

Details:

[http://ubuntuforums.org/showthread.php?t=1033566](http://ubuntuforums.org/showthread.php?t=1033566)

---

### Post by klange on 2009-01-19
The only thing I can really see is an instruction error, which means faulty hardware (a cold boot may fix it, but I can't say for sure). Other than that, DRI is still initializing so, I've got nothing.

---

### Post by thread on 2009-01-19
I know the hw is good because this worked when I originally installed CrunchBang linux. It must have broke when I did a system update.

Also, I just shut the computer, took the battery out, and waited a good 10 seconds before reinserting the battery and turning the machine back on. :) I'd say we could rule that theory out also.

---

### Post by klange on 2009-01-19
Just got on my old laptop and checked things out: I get the same thing, and I am thoroughly confused. Not because it's using the software rasterizer (that could just be because of a broken Mesa stack), but because everything still works. Only slowly. Everything I've ever read or been told as a Compiz dev says this shouldn't be happening, yet I get Compiz, and proper GL handling (like DRI2, only more solid, like a slow nvidia I guess).

This is way out of my league.

**e**: Just got a quick lesson in indirect rendering, and then checked some DRI device permissions.
Try this:
```
sudo chmod a+rwx /dev/dri/card0
```

---

### Post by thread on 2009-01-19
Looks like that did it, WindowsSucks! Thanks very much!

---

### Post by MacUntu on 2009-01-20
[damn, wrong thread]

---

### Post by klange on 2009-01-20
OP updated with fix for software rasterizer issue.
Fun fact: If your GL apps run with the software rasterizer and your compositor runs with hardare (ie, with indirect rendering and the permissions bug present), your GL apps will be redirected because they will be rendered to the X windows directly, not to the screen, no DRI2 required. Of course, it's also painfully slow.

---

### Post by spanishnerd on 2009-02-28
Hi, I have Issue#3, when I try to make the /dev/dri solution it says that the directory does not exist, what should I do?

I have Ubuntu 9.04 latest Alpha (I have update a couple mins ago), Kernel 2.6.28, Intel GMA945.

Thanks in advance.

---

