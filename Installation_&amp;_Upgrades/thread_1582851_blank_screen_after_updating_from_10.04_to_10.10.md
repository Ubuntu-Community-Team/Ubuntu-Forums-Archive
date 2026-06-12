---
title: "blank screen after updating from 10.04 to 10.10"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by netlord on 2010-09-27
hi forum

i´ve tried to update my test-laptop (thinkpad t43) to the actual beta.
the dist-upgrade worked whitout problems, but after rebooting the x-server seems to work, but screen is empty...

it seems that the xserver is crashing:

> Caught signal 11 (Segmentation fault). Server aborting

here the full log:
> [   181.280] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   181.285] X Protocol Version 11, Revision 0
[   181.287] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   181.289] Current Operating System: Linux excelsior 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[   181.290] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=c3b575e6-6893-46f2-ab9b-c9cd24db12e1 ro quiet splash
[   181.292] Build Date: 16 September 2010  05:39:22PM
[   181.294] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   181.296] Current version of pixman: 0.18.4
[   181.298] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   181.301] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   181.307] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 23 16:03:32 2010
[   181.309] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   181.311] (==) No Layout section.  Using the first Screen section.
[   181.311] (==) No screen section available. Using defaults.
[   181.311] (**) |-->Screen "Default Screen Section" (0)
[   181.311] (**) |   |-->Monitor "<default monitor>"
[   181.311] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   181.311] (==) Automatically adding devices
[   181.311] (==) Automatically enabling devices
[   181.311] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   181.311] 	Entry deleted from font path.
[   181.311] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   181.311] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   181.311] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   181.311] (II) Loader magic: 0x81f8e00
[   181.311] (II) Module ABI versions:
[   181.311] 	X.Org ANSI C Emulation: 0.4
[   181.311] 	X.Org Video Driver: 8.0
[   181.311] 	X.Org XInput driver : 11.0
[   181.311] 	X.Org Server Extension : 4.0
[   181.312] (--) PCI:*(0:1:0:0) 1002:5460:1014:056e rev 0, Mem @ 0xc0000000/134217728, 0xa8100000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[   181.312] (II) Open ACPI successful (/var/run/acpid.socket)
[   181.312] (II) LoadModule: "extmod"
[   181.313] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   181.313] (II) Module extmod: vendor="X.Org Foundation"
[   181.313] 	compiled for 1.9.0, module version = 1.0.0
[   181.313] 	Module class: X.Org Server Extension
[   181.313] 	ABI class: X.Org Server Extension, version 4.0
[   181.313] (II) Loading extension MIT-SCREEN-SAVER
[   181.313] (II) Loading extension XFree86-VidModeExtension
[   181.313] (II) Loading extension XFree86-DGA
[   181.313] (II) Loading extension DPMS
[   181.313] (II) Loading extension XVideo
[   181.313] (II) Loading extension XVideo-MotionCompensation
[   181.313] (II) Loading extension X-Resource
[   181.313] (II) LoadModule: "dbe"
[   181.313] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   181.313] (II) Module dbe: vendor="X.Org Foundation"
[   181.313] 	compiled for 1.9.0, module version = 1.0.0
[   181.313] 	Module class: X.Org Server Extension
[   181.313] 	ABI class: X.Org Server Extension, version 4.0
[   181.313] (II) Loading extension DOUBLE-BUFFER
[   181.313] (II) LoadModule: "glx"
[   181.313] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   181.314] (II) Module glx: vendor="X.Org Foundation"
[   181.314] 	compiled for 1.9.0, module version = 1.0.0
[   181.314] 	ABI class: X.Org Server Extension, version 4.0
[   181.314] (==) AIGLX enabled
[   181.314] (II) Loading extension GLX
[   181.314] (II) LoadModule: "record"
[   181.314] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   181.314] (II) Module record: vendor="X.Org Foundation"
[   181.314] 	compiled for 1.9.0, module version = 1.13.0
[   181.314] 	Module class: X.Org Server Extension
[   181.314] 	ABI class: X.Org Server Extension, version 4.0
[   181.314] (II) Loading extension RECORD
[   181.314] (II) LoadModule: "dri"
[   181.314] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   181.314] (II) Module dri: vendor="X.Org Foundation"
[   181.314] 	compiled for 1.9.0, module version = 1.0.0
[   181.314] 	ABI class: X.Org Server Extension, version 4.0
[   181.314] (II) Loading extension XFree86-DRI
[   181.314] (II) LoadModule: "dri2"
[   181.314] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   181.314] (II) Module dri2: vendor="X.Org Foundation"
[   181.314] 	compiled for 1.9.0, module version = 1.2.0
[   181.315] 	ABI class: X.Org Server Extension, version 4.0
[   181.315] (II) Loading extension DRI2
[   181.315] (==) Matched ati as autoconfigured driver 0
[   181.315] (==) Matched vesa as autoconfigured driver 1
[   181.315] (==) Matched fbdev as autoconfigured driver 2
[   181.315] (==) Assigned the driver to the xf86ConfigLayout
[   181.315] (II) LoadModule: "ati"
[   181.315] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   181.315] (II) Module ati: vendor="X.Org Foundation"
[   181.315] 	compiled for 1.9.0, module version = 6.13.1
[   181.315] 	Module class: X.Org Video Driver
[   181.315] 	ABI class: X.Org Video Driver, version 8.0
[   181.315] (II) LoadModule: "radeon"
[   181.315] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   181.316] (II) Module radeon: vendor="X.Org Foundation"
[   181.316] 	compiled for 1.9.0, module version = 6.13.1
[   181.316] 	Module class: X.Org Video Driver
[   181.316] 	ABI class: X.Org Video Driver, version 8.0
[   181.316] (II) LoadModule: "vesa"
[   181.316] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   181.316] (II) Module vesa: vendor="X.Org Foundation"
[   181.316] 	compiled for 1.8.99.905, module version = 2.3.0
[   181.316] 	Module class: X.Org Video Driver
[   181.316] 	ABI class: X.Org Video Driver, version 8.0
[   181.316] (II) LoadModule: "fbdev"
[   181.316] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   181.316] (II) Module fbdev: vendor="X.Org Foundation"
[   181.316] 	compiled for 1.8.99.905, module version = 0.4.2
[   181.316] 	ABI class: X.Org Video Driver, version 8.0
[   181.316] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
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
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
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
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[   181.320] (II) VESA: driver for VESA chipsets: vesa
[   181.320] (II) FBDEV: driver for framebuffer: fbdev
[   181.320] (--) using VT number 7

[   181.327] (II) [KMS] Kernel modesetting enabled.
[   181.327] (WW) Falling back to old probe method for vesa
[   181.327] (WW) Falling back to old probe method for fbdev
[   181.327] (II) Loading sub module "fbdevhw"
[   181.327] (II) LoadModule: "fbdevhw"
[   181.327] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   181.327] (II) Module fbdevhw: vendor="X.Org Foundation"
[   181.327] 	compiled for 1.9.0, module version = 0.0.2
[   181.327] 	ABI class: X.Org Video Driver, version 8.0
[   181.327] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   181.327] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   181.327] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   181.327] (==) RADEON(0): Default visual is TrueColor
[   181.327] (==) RADEON(0): RGB weight 888
[   181.327] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   181.327] (--) RADEON(0): Chipset: "ATI Radeon Mobility X300 (M22) 5460 (PCIE)" (ChipID = 0x5460)
[   181.327] (II) RADEON(0): PCIE card detected
[   181.327] (II) RADEON(0): KMS Color Tiling: enabled
[   181.327] drmOpenDevice: node name is /dev/dri/card0
[   181.327] drmOpenDevice: open result is 9, (OK)
[   181.327] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   181.328] drmOpenDevice: node name is /dev/dri/card0
[   181.328] drmOpenDevice: open result is 9, (OK)
[   181.328] drmOpenByBusid: drmOpenMinor returns 9
[   181.328] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   181.340] (II) RADEON(0): Output VGA-0 has no monitor section
[   181.344] (II) RADEON(0): Output DVI-0 has no monitor section
[   181.344] (II) RADEON(0): Output LVDS has no monitor section
[   181.364] (II) RADEON(0): Output S-video has no monitor section
[   181.372] (II) RADEON(0): EDID for output VGA-0
[   181.376] (II) RADEON(0): EDID for output DVI-0
[   181.376] (II) RADEON(0): EDID for output LVDS
[   181.376] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[   181.376] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "1024x768i" (interlace mode not supported)
[   181.376] (II) RADEON(0): Not using default mode "512x384i" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[   181.377] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[   181.377] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[   181.377] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[   181.377] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[   181.378] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[   181.378] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[   181.378] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[   181.378] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[   181.378] (II) RADEON(0): Printing probed modes for output LVDS
[   181.378] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 770 776 806 (48.4 kHz)
[   181.378] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   181.378] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   181.378] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   181.378] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   181.378] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[   181.378] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[   181.378] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   181.378] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   181.398] (II) RADEON(0): EDID for output S-video
[   181.398] (II) RADEON(0): Output VGA-0 disconnected
[   181.398] (II) RADEON(0): Output DVI-0 disconnected
[   181.398] (II) RADEON(0): Output LVDS connected
[   181.398] (II) RADEON(0): Output S-video disconnected
[   181.398] (II) RADEON(0): Using exact sizes for initial modes
[   181.398] (II) RADEON(0): Output LVDS using initial mode 1024x768
[   181.398] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   181.398] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:4000000 visible:3cc0000
[   181.398] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[   181.398] (==) RADEON(0): DPI set to (96, 96)
[   181.398] (II) Loading sub module "fb"
[   181.398] (II) LoadModule: "fb"
[   181.398] (II) Loading /usr/lib/xorg/modules/libfb.so
[   181.398] (II) Module fb: vendor="X.Org Foundation"
[   181.398] 	compiled for 1.9.0, module version = 1.0.0
[   181.398] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   181.398] (II) Loading sub module "ramdac"
[   181.398] (II) LoadModule: "ramdac"
[   181.398] (II) Module "ramdac" already built-in
[   181.398] (II) Loading sub module "exa"
[   181.398] (II) LoadModule: "exa"
[   181.398] (II) Loading /usr/lib/xorg/modules/libexa.so
[   181.398] (II) Module exa: vendor="X.Org Foundation"
[   181.398] 	compiled for 1.9.0, module version = 2.5.0
[   181.398] 	ABI class: X.Org Video Driver, version 8.0
[   181.399] (II) UnloadModule: "vesa"
[   181.399] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   181.399] (II) UnloadModule: "fbdev"
[   181.399] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   181.399] (II) UnloadModule: "fbdevhw"
[   181.399] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   181.399] (--) Depth 24 pixmap format is 32 bpp
[   181.399] (II) RADEON(0): [DRI2] Setup complete
[   181.399] (II) RADEON(0): [DRI2]   DRI driver: r300
[   181.399] (II) RADEON(0): Front buffer size: 3072K
[   181.399] (II) RADEON(0): VRAM usage limit set to 53222K
[   181.399] (==) RADEON(0): Backing store disabled
[   181.399] (II) RADEON(0): Direct rendering enabled
[   181.399] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[   181.399] (II) RADEON(0): Setting EXA maxPitchBytes
[   181.399] (II) EXA(0): Driver allocated offscreen pixmaps
[   181.399] (II) EXA(0): Driver registered support for the following operations:
[   181.399] (II)         Solid
[   181.399] (II)         Copy
[   181.399] (II)         Composite (RENDER acceleration)
[   181.399] (II)         UploadToScreen
[   181.399] (II)         DownloadFromScreen
[   181.399] (II) RADEON(0): Acceleration enabled
[   181.399] (==) RADEON(0): DPMS enabled
[   181.399] (==) RADEON(0): Silken mouse enabled
[   181.399] (II) RADEON(0): Set up textured video
[   181.399] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   181.399] (--) RandR disabled
[   181.399] (II) Initializing built-in extension Generic Event Extension
[   181.399] (II) Initializing built-in extension SHAPE
[   181.399] (II) Initializing built-in extension MIT-SHM
[   181.399] (II) Initializing built-in extension XInputExtension
[   181.399] (II) Initializing built-in extension XTEST
[   181.399] (II) Initializing built-in extension BIG-REQUESTS
[   181.399] (II) Initializing built-in extension SYNC
[   181.399] (II) Initializing built-in extension XKEYBOARD
[   181.400] (II) Initializing built-in extension XC-MISC
[   181.400] (II) Initializing built-in extension SECURITY
[   181.400] (II) Initializing built-in extension XINERAMA
[   181.400] (II) Initializing built-in extension XFIXES
[   181.400] (II) Initializing built-in extension RENDER
[   181.400] (II) Initializing built-in extension RANDR
[   181.400] (II) Initializing built-in extension COMPOSITE
[   181.400] (II) Initializing built-in extension DAMAGE
[   181.400] (II) Initializing built-in extension GESTURE
[   181.417] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   181.417] (II) AIGLX: enabled GLX_INTEL_swap_event
[   181.417] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   181.417] (II) AIGLX: enabled GLX_SGI_make_current_read
[   181.417] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   181.417] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[   181.418] (II) GLX: Initialized DRI2 GL provider for screen 0
[   181.418] (II) RADEON(0): Setting screen physical size to 270 x 203
[   181.446] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   181.509] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   181.509] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   181.509] (II) LoadModule: "evdev"
[   181.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   181.510] (II) Module evdev: vendor="X.Org Foundation"
[   181.510] 	compiled for 1.9.0, module version = 2.3.2
[   181.510] 	Module class: X.Org XInput Driver
[   181.510] 	ABI class: X.Org XInput driver, version 11.0
[   181.510] (**) Power Button: always reports core events
[   181.510] (**) Power Button: Device: "/dev/input/event2"
[   181.510] (II) Power Button: Found keys
[   181.510] (II) Power Button: Configuring as keyboard
[   181.510] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   181.510] (**) Option "xkb_rules" "evdev"
[   181.511] (**) Option "xkb_model" "pc105"
[   181.511] (**) Option "xkb_layout" "de"
[   181.511] (**) Option "xkb_variant" "nodeadkeys"
[   181.514] (II) XKB: generating xkmfile /tmp/server-76D2B5A359D34EEB9BFAEB1701EF70014DF39715.xkm
[   181.542] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   181.542] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   181.542] (**) Video Bus: always reports core events
[   181.542] (**) Video Bus: Device: "/dev/input/event5"
[   181.542] (II) Video Bus: Found keys
[   181.542] (II) Video Bus: Configuring as keyboard
[   181.542] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   181.542] (**) Option "xkb_rules" "evdev"
[   181.542] (**) Option "xkb_model" "pc105"
[   181.542] (**) Option "xkb_layout" "de"
[   181.542] (**) Option "xkb_variant" "nodeadkeys"
[   181.543] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   181.543] (II) No input driver/identifier specified (ignoring)
[   181.543] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   181.543] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   181.543] (**) Sleep Button: always reports core events
[   181.543] (**) Sleep Button: Device: "/dev/input/event1"
[   181.543] (II) Sleep Button: Found keys
[   181.543] (II) Sleep Button: Configuring as keyboard
[   181.543] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   181.543] (**) Option "xkb_rules" "evdev"
[   181.543] (**) Option "xkb_model" "pc105"
[   181.543] (**) Option "xkb_layout" "de"
[   181.543] (**) Option "xkb_variant" "nodeadkeys"
[   181.549] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   181.549] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   181.549] (**) AT Translated Set 2 keyboard: always reports core events
[   181.549] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   181.549] (II) AT Translated Set 2 keyboard: Found keys
[   181.549] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   181.549] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   181.549] (**) Option "xkb_rules" "evdev"
[   181.549] (**) Option "xkb_model" "pc105"
[   181.549] (**) Option "xkb_layout" "de"
[   181.549] (**) Option "xkb_variant" "nodeadkeys"
[   181.550] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[   181.550] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   181.550] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   181.550] (II) LoadModule: "synaptics"
[   181.550] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   181.550] (II) Module synaptics: vendor="X.Org Foundation"
[   181.550] 	compiled for 1.9.0, module version = 1.2.2
[   181.550] 	Module class: X.Org XInput Driver
[   181.550] 	ABI class: X.Org XInput driver, version 11.0
[   181.550] (II) Synaptics touchpad driver version 1.2.2
[   181.550] (**) Option "Device" "/dev/input/event4"
[   181.550] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   181.550] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   181.550] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   181.550] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   181.550] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   181.551] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   181.551] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   181.551] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   181.551] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   181.551] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   181.551] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   181.551] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   181.551] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   181.551] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   181.551] (II) No input driver/identifier specified (ignoring)
[   181.551] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[   181.552] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[   181.552] (**) TPPS/2 IBM TrackPoint: always reports core events
[   181.552] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[   181.552] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[   181.552] (II) TPPS/2 IBM TrackPoint: Found relative axes
[   181.552] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[   181.552] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[   181.552] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[   181.552] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   181.552] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[   181.552] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[   181.552] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[   181.552] (II) No input driver/identifier specified (ignoring)
[   181.553] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[   181.553] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[   181.553] (**) ThinkPad Extra Buttons: always reports core events
[   181.553] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[   181.553] (II) ThinkPad Extra Buttons: Found keys
[   181.553] (II) ThinkPad Extra Buttons: Configuring as keyboard
[   181.553] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[   181.553] (**) Option "xkb_rules" "evdev"
[   181.553] (**) Option "xkb_model" "pc105"
[   181.553] (**) Option "xkb_layout" "de"
[   181.553] (**) Option "xkb_variant" "nodeadkeys"
[   183.880] (II) RADEON(0): Allocate new frame buffer 1360x768 stride 1408
[   183.880] (II) RADEON(0): VRAM usage limit set to 52185K
[   205.531] (II) AIGLX: Suspending AIGLX clients for VT switch
[   350.354] 
Backtrace:
[   350.371] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
[   350.385] 1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
[   350.387] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x27540c]
[   350.397] 3: /usr/bin/X (FreeClientResources+0xed) [0x808f04d]
[   350.399] 4: /usr/bin/X (FreeAllResources+0x60) [0x808f120]
[   350.405] 5: /usr/bin/X (0x8048000+0x1a5e6) [0x80625e6]
[   350.407] 6: /lib/libc.so.6 (__libc_start_main+0xe7) [0x45ece7]
[   350.415] 7: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
[   350.417] Segmentation fault at address (nil)
[   350.418] 
Caught signal 11 (Segmentation fault). Server aborting
[   350.430] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   350.445] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   350.447] 
[   350.454] (II) ThinkPad Extra Buttons: Close
[   350.454] (II) UnloadModule: "evdev"
[   350.454] (II) TPPS/2 IBM TrackPoint: Close
[   350.454] (II) UnloadModule: "evdev"
[   350.454] (II) UnloadModule: "synaptics"
[   350.454] (II) AT Translated Set 2 keyboard: Close
[   350.454] (II) UnloadModule: "evdev"
[   350.454] (II) Sleep Button: Close
[   350.454] (II) UnloadModule: "evdev"
[   350.455] (II) Video Bus: Close
[   350.455] (II) UnloadModule: "evdev"
[   350.455] (II) Power Button: Close
[   350.455] (II) UnloadModule: "evdev"
[   350.455]  ddxSigGiveUp: Closing log


i´ve also tried to install the fglrx-driver, but the install failed.

what can i do?

---

### Post by Fafler on 2010-09-27
I had the same error with the radeon driver from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Downgraded to the radeon driver from the Ubuntu repository and now it works.
If you use the same drivers as me, do a ppa-purge xorg-edgers to fix it.

---

### Post by netlord on 2010-09-28
> **Fafler said:**
> If you use the same drivers as me, do a ppa-purge xorg-edgers to fix it.

i never used this driver.

however - after removing the xserver-xorg-video-radeon and xorg-xserver-video-ati the x-server started.

i can see a desktop - probably slower then it could be - but im glad its working so far.

thx

---

### Post by Terc on 2010-10-06
I can confirm that this is also an issue on my Acer 2010wlmi with radeon mobility 9250.

I had this issue while attempting to install 10.10 beta from the install cd.  Really disappointing.

---

### Post by Terc on 2010-10-06
I've discovered the issue - Ubuntu has chosen my external monitor as the primary display even though no monitor was attached. The workaround was easy enough for me - plug in an external monitor and complete the install.  I'll post back when the install is completed.  I'm assuming I'll need to keep the external attached, then reconfigure my monitors to set the connected display as the primary.

---

### Post by Terc on 2010-10-06
Actually, I just finished my install and the problem is much more clear now.

For some reason, my lcd panel is being detected as 1360x768 (or at least  set to that by default).  This is a problem since it can't display that resolution (it's actually 1280x800).  After attaching an external monitor and configuring the correct resolution, things are working just fine.  Actually, better than they've worked before - I finally get 3d accel out of the box on this old graphics card (ATI mobility 9250).  This is great!  Now if somehow it would just detect the proper resolution out of the box, I'd be a very happy user.

Edit:

One more problem.  I cannot set this configuration to be the default.  This means my logon screen is still using the incorrect settings (and I assume, any future user will have the same issue).  When I click on Make Default in the gnome-display-properties dialog box, I get an error: GtK-WARNING **: No object called:
/etc/gnome-settings-daemon/xrandr must be a directory

I might be able to work around this by setting my laptop to log in automatically, but hopefully this can be fixed before the final release.  The installer is looking great, I see major visual improvements everywhere, and I'm looking forward to stepping on some landmines in btrfs territory too.

I see this bug has already been filed: [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg467439.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg467439.html)

Still, an additional bug for Radeo 9250 users - improper video resolution detection.

---

