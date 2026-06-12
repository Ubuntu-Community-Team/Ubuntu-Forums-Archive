---
title: "Monitor goes into standby during boot sequence"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2008-09-02
Trying to load the 2 Sep Intrepid daily (IA-32) after being away for a couple of weeks. I lose video output and the display goes to standby during the IPL sequence for both the live desktop or install procedures. 

Removing "splash" and "quiet" from the boot options, the last thing I see is (briefly) the text mode login prompt, then the screen blanks and the "standby" mode LED on the display lights.  The machine continues to read from the CD for some time.  

When that stops <ctrl><alt><F3> opens a terminal. Issuing "startx" indicates the server is already running. <ctrl><alt><F7> reqults in blank screen followed by the display returning to standby mode. 

Hardy works flawlessly on this machine, and I did not have this problem with either the alpha-3 release for both Ubuntu and Kbuntu. 

Any ideas?

---

### Post by Nullack on 2008-09-02
Have a look at your x logs

---

### Post by rbmorse on 2008-09-02
When trying to start the live Desktop session, Xorg logs appear pretty nominal. No errors (EE) reported.  No unexpected warnings for the video card in use (ATI HD3870) (acceleration could not be enabled). 

The radeon driver is loaded.

The video card is detected, properly identified and initialized

The display (Apple Cinema HD 23 inch) s correctly identified and DAC decoded (many times, in fact, but I don't know if that's normal or not). 

I don't see modlines for 1920 X 1200 @ 60Hz or 1920 X 1200 @ 72Hz. 1920X1200@74 is a valid mode for this unit, I'm not sure about 1920X1200@74.5 Hz

Perhaps someone more knowledgable than I may see something useful:

> (WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.99.906 (1.5.0 RC 6)
Release Date: 
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-2-generic #1 SMP Thu Aug 28 17:20:02 UTC 2008 i686
Build Date: 01 September 2008  11:33:42PM
xorg-server 2:1.4.99.906-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep  2 22:49:58 2008
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
(II) Loader magic: 0x81d8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Radeon HD 3870 rev 0, Mem @ 0xe0000000/0, 0xf5000000/0, I/O @ 0x0000b000/0, BIOS @ 0x????????/131072
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
	compiled for 1.4.99.906, module version = 1.0.0
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
	compiled for 1.4.99.906, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.99.906, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:00:0
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
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000f5000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon HD3870" (ChipID = 0x9501)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1458 SubsystemID: 0x2198
	IOBaseAddress: 0xb000
	Filename: Test.bin    
	BIOS Bootup Message: GV-RX387512H_F22                         

                       
(II) RADEON(0): Framebuffer space used by Firmware (kb): 16
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffc000
(II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffc000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 780000
(II) RADEON(0): Default Memory Clock: 950000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(II) RADEON(0): Direct rendering not officially supported on RN50/RS600/R600
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (256 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 780.000000, mclk: 950.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 000f 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 0011 01
src object id 2114 20
record type 4
record type 11
object id 0011 01
src object id 2114 20
record type 4
record type 11
(II) RADEON(0): Output DVI-1 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- LVTMA
 DDC Type  -- 0x7e40
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): Panel infos found from DDC detailed: 1920x1200
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output DVI-1 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-1 using initial mode 1920x1200
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (490, 310) mm
(**) RADEON(0): DPI set to (99, 131)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
mc fb loc is 00ff00e0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1920,8191)
(II) RADEON(0): Reserved area from (0,1600) to (1920,1602)
(II) RADEON(0): Largest offscreen area available: 1920 x 6589
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1920x1200 - 2080 1235 9
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 154000000
best_freq: 154000000
best_feedback_div: 308
best_ref_div: 9
best_post_div: 6
(II) RADEON(0): crtc(0) Clock: mode 154000, PLL 154000
(II) RADEON(0): crtc(0) PLL  : refdiv 9, fbdiv 0x134(308), pdiv 6
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output TMDS1 setup success
Output 66 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1602)
(II) RADEON(0): Using hardware cursor 1 (scanline 1604)
(II) RADEON(0): Largest offscreen area available: 1920 x 6584
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 495 x 310
Enable CRTC 0 success
Unblank CRTC 0 success
Output 66 enable success
(II) config/hal: Adding input device ImExPS/2 Logitech Explorer Mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 2.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) ImExPS/2 Logitech Explorer Mouse: always reports core events
(**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Explorer Mouse: Found mouse buttons
(II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "base"
(**) AT Translated Set 2 keyboard: xkb_rules: "base"
(**) Option "xkb_model" "evdev"
(**) AT Translated Set 2 keyboard: xkb_model: "evdev"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0  193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-1 ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 921c  Serial#: 33656039
(II) RADEON(0): Year: 2008  Week: 11
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 49  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off(II) RADEON(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.618
(II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  495 x 310 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: 2A8111QSXMN
(II) RADEON(0): Monitor name: Cinema HD
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006101c92e78c0102
(II) RADEON(0): 	0b12010380311f782efd45a3574a9e25
(II) RADEON(0): 	135054000000d1000101010101010101
(II) RADEON(0): 	010101010101283c80a070b023403020
(II) RADEON(0): 	3600ef361100001a000000ff00324138
(II) RADEON(0): 	3131315153584d4e0a20000000fc0043
(II) RADEON(0): 	696e656d612048440a20202000000000
(II) RADEON(0): 	0000000000000000000000000000011b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "APP", prod id 37404
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ff00e0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
(II) RADEON(0): avivo_restore !
Enable CRTC 0 success
Unblank CRTC 0 success

---

### Post by RAOF on 2008-09-02
> 

(II) RADEON(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) RADEON(0): Modeline "1920x1200"x60.0 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync (74.5 kHz)


Looks a bit suspicious to me - it looks like you've got two modelines for the same mode, one of which appears to have a refresh rate of 0.0Hz.  Furthermore, it looks like X is selecting this mode, which I'd guess is actually invalid.

Since you can get at a terminal, can you run
```

DISPLAY=:0 xrandr -q

```
which should get you a list of modes for your screen.  If you could paste that here, it'd be great.

Anyway, this seems like a pretty clear-cut bug.  The end result of this will be a bug filed against xserver-xorg-video-ati on Launchpad ;).

---

### Post by rbmorse on 2008-09-02
Heres the output from DISPLAY=:0 xrandr -q

> Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 1920 x 1600
DVI-1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 495mm x 310mm
   1920x1200      60.0*+   60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)

Thank you for your assistance.

---

### Post by RAOF on 2008-09-02
You should be able to get X to display *something* by running
```

DISPLAY=:0 xrandr --output DVI-1 --mode 1600x1200x60

```
(or some other mode) and then switching back to X.  You might also want to try running
```

DISPLAY=:0 xrandr --verbose -q

```
to get a lot more detail; I can't really see what's wrong with that.  It might be time to move to a launchpad bug.

---

### Post by RAOF on 2008-09-02
You should be able to get X to display *something* by running
```

DISPLAY=:0 xrandr --output DVI-1 --mode 1600x1200x60

```
(or some other mode) and then switching back to X.  You might also want to try running
```

DISPLAY=:0 xrandr --verbose -q

```
to get a lot more detail; I can't really see what's wrong with that.  It might be time to move to a launchpad bug.

---

### Post by rbmorse on 2008-09-02
Here's the verbose output from DISPLAY=:0 --verbose -q
>  Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 1920 x 1600
DVI-1 connected 1920x1200+0+0 (0x3d) normal (normal left inverted right x axis y axis) 495mm x 310mm
	Identifier: 0x3b
	Timestamp:  128297
	Subpixel:   horizontal rgb
	Clones:     DVI-0
	CRTC:       0
	CRTCs:      0 1
	EDID_DATA:
		00ffffffffffff0006101c92e78c0102
		0b12010380311f782efd45a3574a9e25
		135054000000d1000101010101010101
		010101010101283c80a070b023403020
		3600ef361100001a000000ff00324138
		3131315153584d4e0a20000000fc0043
		696e656d612048440a20202000000000
		0000000000000000000000000000011b
		dvi_monitor_type: auto
		scaler: off
		tmds_pll: bios
	load_detection: 1 (0x00000001) range:  (0,1)
  1920x1200 (0x3d)  154.0MHz +HSync -VSync *current +preferred
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   74.0KHz
        v: height 1200 start 1203 end 1209 total 1235           clock   60.0Hz
  1920x1200 (0x3e)  193.2MHz -HSync +VSync
        h: width  1920 start 2048 end 2256 total 2592 skew    0 clock   74.5KHz
        v: height 1200 start 1201 end 1204 total 1242           clock   60.0Hz
  1600x1200 (0x3f)  162.0MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1680x1050 (0x40)  146.2MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1600x1024 (0x41)  103.1MHz +HSync +VSync
        h: width  1600 start 1600 end 1656 total 1664 skew    0 clock   62.0KHz
        v: height 1024 start 1024 end 1029 total 1030           clock   60.2Hz
  1400x1050 (0x42)  122.0MHz +HSync +VSync
        h: width  1400 start 1488 end 1640 total 1880 skew    0 clock   64.9KHz
        v: height 1050 start 1052 end 1064 total 1082           clock   60.0Hz
  1280x1024 (0x43)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1440x900 (0x44)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0x45)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1360x768 (0x46)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1152x864 (0x47)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x48)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x49)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4a)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DVI-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3c
	Timestamp:  128297
	Subpixel:   no subpixels
	Clones:     DVI-1
	CRTCs:      0 1
		dvi_monitor_type: auto
		scaler: off
	load_detection: 1 (0x00000001) range:  (0,1)

---

### Post by RAOF on 2008-09-02
Hm.  Maybe try
```

DISPLAY=:0 xrandr --output DVI-1 --mode 0x3e

```
and switch back to X?

---

### Post by rbmorse on 2008-09-02
> **RAOF said:**
> Hm.  Maybe try
```

DISPLAY=:0 xrandr --output DVI-1 --mode 0x3e

```
and switch back to X?
That one produces:
> Configure ctrc0 failed

Just for fun I tried to send the command to DVI-0 and that returned
>  cannot find mode 0x3e

---

### Post by rbmorse on 2008-09-03
I have the live Desktop going by booting from the disc and blindly waiting for activity to finish, then editing xorg.conf with nano in a text session to load the vesa driver for the default video device.  Save, exit, switch to the "X" screen and <ctrl><alt><backspace> to restart "X" and I have a display. 

I"m going to install to the hard drive from here, and see if the default radeon driver works better if started from the hard drive rather than the live CD. 

There appears to be a bug here, but I'm not sure if it is somewhere in "X", randr or the xf-86-video-ati driver. 

Many thanks for you assistance.

---

### Post by rbmorse on 2008-09-03
To followup, the installation to hard drive boots nominally, i.e., the desktop appears as expected with the vesa or radeonhd drivers specified in xorg.conf.  I'll try the default configuration (no driver specified for the default video device).

---

### Post by rbmorse on 2008-09-03
I just tried booting with no driver specified in xorg.conf, the installation default. On my machine this loads the "radeon" driver (xserver-xorg-video-ati) and the display shutdown durning the boot sequence as described in the OP. 

Switching back to the radeonhd driver returns normal operation. 

So, it appears to me the problem lies somewhere in the version of the radeon driver that is part of the current daily live-desktop shipset.

---

### Post by rbmorse on 2008-09-03
Bug 264462 filed against Ubuntu daily CD images as my guess is the radeon driver (from the radeon git) needs to be updated in the liveCD build.

---

