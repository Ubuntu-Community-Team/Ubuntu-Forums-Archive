---
title: "Xorg stopped working following upgrade"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by olly3 on 2015-10-18
Hi, yesterday I did an upgrade, specifically sudo apt-get upgrade. However, when I started up my machine this morning, I got an error message saying something along the lines of "Xorg is not working". And so now my graphical user interface does not work. I just get a black screen. I can get to the command line usin gthe ctrl-f4 shortcut or whatever it is. 

I have absolutely no idea how to fix this - I'm in over my head here as a newbie. I have copied the contents of the Xorg.0.log file in the hope that somebody here may be able to diagnose the problem: 

```
[    29.661] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.661] X Protocol Version 11, Revision 0
[    29.661] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    29.661] Current Operating System: Linux olly 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64
[    29.661] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=f340b098-6f9c-4079-b7c1-fb45f9e9ed52 ro quiet splash nomodeset vt.handoff=7
[    29.661] Build Date: 12 February 2015  02:49:29PM
[    29.661] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    29.661] Current version of pixman: 0.30.2
[    29.661] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    29.661] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.662] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 18 14:52:25 2015
[    29.662] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.663] (==) No Layout section.  Using the first Screen section.
[    29.663] (==) No screen section available. Using defaults.
[    29.663] (**) |-->Screen "Default Screen Section" (0)
[    29.663] (**) |   |-->Monitor "<default monitor>"
[    29.664] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    29.664] (==) Automatically adding devices
[    29.664] (==) Automatically enabling devices
[    29.664] (==) Automatically adding GPU devices
[    29.664] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.664] 	Entry deleted from font path.
[    29.664] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.664] 	Entry deleted from font path.
[    29.664] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.664] 	Entry deleted from font path.
[    29.664] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.664] 	Entry deleted from font path.
[    29.664] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.664] 	Entry deleted from font path.
[    29.664] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    29.664] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.665] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.665] (II) Loader magic: 0x7f0a56e70d40
[    29.665] (II) Module ABI versions:
[    29.665] 	X.Org ANSI C Emulation: 0.4
[    29.665] 	X.Org Video Driver: 15.0
[    29.665] 	X.Org XInput driver : 20.0
[    29.665] 	X.Org Server Extension : 8.0
[    29.668] (--) PCI:*(0:0:1:0) 1002:9851:103c:22cd rev 5, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xf0e00000/262144, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    29.668] Initializing built-in extension Generic Event Extension
[    29.668] Initializing built-in extension SHAPE
[    29.668] Initializing built-in extension MIT-SHM
[    29.668] Initializing built-in extension XInputExtension
[    29.668] Initializing built-in extension XTEST
[    29.668] Initializing built-in extension BIG-REQUESTS
[    29.668] Initializing built-in extension SYNC
[    29.668] Initializing built-in extension XKEYBOARD
[    29.669] Initializing built-in extension XC-MISC
[    29.669] Initializing built-in extension SECURITY
[    29.669] Initializing built-in extension XINERAMA
[    29.669] Initializing built-in extension XFIXES
[    29.669] Initializing built-in extension RENDER
[    29.669] Initializing built-in extension RANDR
[    29.669] Initializing built-in extension COMPOSITE
[    29.669] Initializing built-in extension DAMAGE
[    29.669] Initializing built-in extension MIT-SCREEN-SAVER
[    29.669] Initializing built-in extension DOUBLE-BUFFER
[    29.669] Initializing built-in extension RECORD
[    29.669] Initializing built-in extension DPMS
[    29.669] Initializing built-in extension Present
[    29.669] Initializing built-in extension DRI3
[    29.669] Initializing built-in extension X-Resource
[    29.669] Initializing built-in extension XVideo
[    29.669] Initializing built-in extension XVideo-MotionCompensation
[    29.669] Initializing built-in extension SELinux
[    29.669] Initializing built-in extension XFree86-VidModeExtension
[    29.669] Initializing built-in extension XFree86-DGA
[    29.669] Initializing built-in extension XFree86-DRI
[    29.669] Initializing built-in extension DRI2
[    29.669] (II) LoadModule: "glx"
[    29.670] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.673] (II) Module glx: vendor="X.Org Foundation"
[    29.673] 	compiled for 1.15.1, module version = 1.0.0
[    29.673] 	ABI class: X.Org Server Extension, version 8.0
[    29.673] (==) AIGLX enabled
[    29.673] Loading extension GLX
[    29.673] (==) Matched fglrx as autoconfigured driver 0
[    29.673] (==) Matched ati as autoconfigured driver 1
[    29.673] (==) Matched modesetting as autoconfigured driver 2
[    29.673] (==) Matched fbdev as autoconfigured driver 3
[    29.673] (==) Matched vesa as autoconfigured driver 4
[    29.673] (==) Assigned the driver to the xf86ConfigLayout
[    29.673] (II) LoadModule: "fglrx"
[    29.673] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    29.708] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    29.708] 	compiled for 1.4.99.906, module version = 14.20.7
[    29.708] 	Module class: X.Org Video Driver
[    29.709] (II) Loading sub module "fglrxdrm"
[    29.709] (II) LoadModule: "fglrxdrm"
[    29.709] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    29.709] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.709] 	compiled for 1.4.99.906, module version = 14.20.7
[    29.709] (II) LoadModule: "ati"
[    29.710] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    29.710] (II) Module ati: vendor="X.Org Foundation"
[    29.710] 	compiled for 1.15.1, module version = 7.3.0
[    29.710] 	Module class: X.Org Video Driver
[    29.710] 	ABI class: X.Org Video Driver, version 15.0
[    29.710] (II) LoadModule: "radeon"
[    29.710] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.711] (II) Module radeon: vendor="X.Org Foundation"
[    29.711] 	compiled for 1.15.1, module version = 7.3.0
[    29.711] 	Module class: X.Org Video Driver
[    29.711] 	ABI class: X.Org Video Driver, version 15.0
[    29.711] (II) LoadModule: "modesetting"
[    29.711] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.711] (II) Module modesetting: vendor="X.Org Foundation"
[    29.711] 	compiled for 1.15.0, module version = 0.8.1
[    29.711] 	Module class: X.Org Video Driver
[    29.711] 	ABI class: X.Org Video Driver, version 15.0
[    29.711] (II) LoadModule: "fbdev"
[    29.712] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.712] (II) Module fbdev: vendor="X.Org Foundation"
[    29.712] 	compiled for 1.15.0, module version = 0.4.4
[    29.712] 	Module class: X.Org Video Driver
[    29.712] 	ABI class: X.Org Video Driver, version 15.0
[    29.712] (II) LoadModule: "vesa"
[    29.712] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.712] (II) Module vesa: vendor="X.Org Foundation"
[    29.712] 	compiled for 1.15.0, module version = 2.3.3
[    29.712] 	Module class: X.Org Video Driver
[    29.712] 	ABI class: X.Org Video Driver, version 15.0
[    29.712] (II) AMD Proprietary Linux Driver Version Identifier:14.20.7
[    29.712] (II) AMD Proprietary Linux Driver Release Identifier: 14.201.1008                          
[    29.712] (II) AMD Proprietary Linux Driver Build Date: Aug 12 2014 09:11:40
[    29.712] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII
[    29.723] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.723] (II) FBDEV: driver for framebuffer: fbdev
[    29.723] (II) VESA: driver for VESA chipsets: vesa
[    29.723] (++) using VT number 8


[    29.728] (WW) Falling back to old probe method for fglrx
[    29.750] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    29.755] ukiDynamicMajor: found major device number 250
[    29.761] (--) Assigning device section with no busID to primary device
[    29.761] (--) Chipset Supported AMD Graphics Processor (0x9851) found
[    29.761] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    29.762] (II) fglrx(0): pEnt->device->identifier=0x7f0a56c0ba97
[    29.762] (WW) Falling back to old probe method for modesetting
[    29.762] (EE) open /dev/dri/card0: No such file or directory
[    29.762] (WW) Falling back to old probe method for fbdev
[    29.762] (II) Loading sub module "fbdevhw"
[    29.762] (II) LoadModule: "fbdevhw"
[    29.763] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.763] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.763] 	compiled for 1.15.1, module version = 0.0.2
[    29.763] 	ABI class: X.Org Video Driver, version 15.0
[    29.763] (WW) Falling back to old probe method for vesa
[    29.763] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    29.763] (II) Loading sub module "vgahw"
[    29.763] (II) LoadModule: "vgahw"
[    29.764] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    29.764] (II) Module vgahw: vendor="X.Org Foundation"
[    29.764] 	compiled for 1.15.1, module version = 0.1.0
[    29.764] 	ABI class: X.Org Video Driver, version 15.0
[    29.765] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    29.765] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    29.765] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.765] (==) fglrx(0): Default visual is TrueColor
[    29.765] (==) fglrx(0): RGB weight 888
[    29.765] (II) fglrx(0): Using 8 bits per RGB 
[    29.765] (==) fglrx(0): Buffer Tiling is ON
[    29.765] (II) Loading sub module "fglrxdrm"
[    29.765] (II) LoadModule: "fglrxdrm"
[    29.765] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    29.765] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.765] 	compiled for 1.4.99.906, module version = 14.20.7
[    29.770] ukiDynamicMajor: found major device number 250
[    29.770] ukiDynamicMajor: found major device number 250
[    29.770] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    29.770] ukiOpenDevice: node name is /dev/ati/card0
[    29.770] ukiOpenDevice: open result is 11, (OK)
[    29.770] ukiOpenByBusid: ukiOpenMinor returns 11
[    29.771] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    29.771] (**) fglrx(0): NoAccel = NO
[    29.771] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    29.771] (--) fglrx(0): Chipset: "AMD Radeon(TM) R5 Graphics         " (Chipset = 0x9851)
[    29.771] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x22cd)
[    29.771] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    29.771] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    29.771] (--) fglrx(0): MMIO registers at 0xf0e00000
[    29.771] (--) fglrx(0): I/O port at 0x00004000
[    29.771] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    29.772] (II) fglrx(0): ATIF platform detected
[    29.772] (II) fglrx(0): AC Adapter is used
[    29.772] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    29.772] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    29.772] (II) fglrx(0): PCIE card detected
[    29.772] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.773] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.773] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x40000000)
[    29.773] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.773] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.773] (II) Loading sub module "fb"
[    29.773] (II) LoadModule: "fb"
[    29.773] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.774] (II) Module fb: vendor="X.Org Foundation"
[    29.774] 	compiled for 1.15.1, module version = 1.0.0
[    29.774] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.774] (II) fglrx(0): EDID Management option: EDID Management is enabled
[    29.774] (II) Loading sub module "ddc"
[    29.774] (II) LoadModule: "ddc"
[    29.774] (II) Module "ddc" already built-in
[    29.830] (II) fglrx(0): Output LVDS has no monitor section
[    29.830] (II) fglrx(0): Output DFP1 has no monitor section
[    29.830] (II) fglrx(0): Output CRT1 has no monitor section
[    29.830] (II) Loading sub module "ddc"
[    29.830] (II) LoadModule: "ddc"
[    29.830] (II) Module "ddc" already built-in
[    29.830] (II) fglrx(0): Connected Display0: LVDS
[    29.830] (II) fglrx(0): Display0 EDID data ---------------------------
[    29.830] (II) fglrx(0): Manufacturer: LGD  Model: 39f  Serial#: 0
[    29.830] (II) fglrx(0): Year: 2012  Week: 0
[    29.830] (II) fglrx(0): EDID Version: 1.4
[    29.830] (II) fglrx(0): Digital Display Input
[    29.830] (II) fglrx(0): 6 bits per channel
[    29.830] (II) fglrx(0): Digital interface is DisplayPort
[    29.830] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    29.830] (II) fglrx(0): Gamma: 2.20
[    29.830] (II) fglrx(0): No DPMS capabilities specified
[    29.830] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.830] (II) fglrx(0): First detailed timing is preferred mode
[    29.830] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[    29.830] (II) fglrx(0): redX: 0.578 redY: 0.344   greenX: 0.337 greenY: 0.571
[    29.831] (II) fglrx(0): blueX: 0.159 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    29.831] (II) fglrx(0): Manufacturer's mask: 0
[    29.831] (II) fglrx(0): Supported detailed timing:
[    29.831] (II) fglrx(0): clock: 76.3 MHz   Image Size:  345 x 194 mm
[    29.831] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    29.831] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    29.831] (II) fglrx(0): Supported detailed timing:
[    29.831] (II) fglrx(0): clock: 50.9 MHz   Image Size:  345 x 194 mm
[    29.831] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    29.831] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    29.831] (II) fglrx(0): Unknown vendor-specific block 2
[    29.831] (II) fglrx(0): EDID (in hex):
[    29.831] (II) fglrx(0): 	00ffffffffffff0030e49f0300000000
[    29.831] (II) fglrx(0): 	00160104952313780a05f59458569228
[    29.831] (II) fglrx(0): 	1e505400000001010101010101010101
[    29.831] (II) fglrx(0): 	010101010101ce1d56f4500016303020
[    29.831] (II) fglrx(0): 	350059c21000001bdf1356f450001630
[    29.831] (II) fglrx(0): 	3020350059c21000001b000000000000
[    29.831] (II) fglrx(0): 	00000000000000000000000000000002
[    29.831] (II) fglrx(0): 	000c4cff0a3c640f131f640000000045
[    29.831] (II) fglrx(0): End of Display0 EDID data --------------------
[    29.831] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    29.832] (II) fglrx(0): EDID for output LVDS
[    29.832] (II) fglrx(0): Manufacturer: LGD  Model: 39f  Serial#: 0
[    29.832] (II) fglrx(0): Year: 2012  Week: 0
[    29.832] (II) fglrx(0): EDID Version: 1.4
[    29.832] (II) fglrx(0): Digital Display Input
[    29.832] (II) fglrx(0): 6 bits per channel
[    29.832] (II) fglrx(0): Digital interface is DisplayPort
[    29.832] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    29.832] (II) fglrx(0): Gamma: 2.20
[    29.832] (II) fglrx(0): No DPMS capabilities specified
[    29.832] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.832] (II) fglrx(0): First detailed timing is preferred mode
[    29.832] (II) fglrx(0): Preferred mode is native pixel format and refresh rate
[    29.832] (II) fglrx(0): redX: 0.578 redY: 0.344   greenX: 0.337 greenY: 0.571
[    29.832] (II) fglrx(0): blueX: 0.159 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    29.832] (II) fglrx(0): Manufacturer's mask: 0
[    29.832] (II) fglrx(0): Supported detailed timing:
[    29.832] (II) fglrx(0): clock: 76.3 MHz   Image Size:  345 x 194 mm
[    29.832] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    29.832] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    29.832] (II) fglrx(0): Supported detailed timing:
[    29.832] (II) fglrx(0): clock: 50.9 MHz   Image Size:  345 x 194 mm
[    29.832] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1610 h_border: 0
[    29.832] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    29.832] (II) fglrx(0): Unknown vendor-specific block 2
[    29.832] (II) fglrx(0): EDID (in hex):
[    29.832] (II) fglrx(0): 	00ffffffffffff0030e49f0300000000
[    29.832] (II) fglrx(0): 	00160104952313780a05f59458569228
[    29.832] (II) fglrx(0): 	1e505400000001010101010101010101
[    29.832] (II) fglrx(0): 	010101010101ce1d56f4500016303020
[    29.832] (II) fglrx(0): 	350059c21000001bdf1356f450001630
[    29.832] (II) fglrx(0): 	3020350059c21000001b000000000000
[    29.832] (II) fglrx(0): 	00000000000000000000000000000002
[    29.833] (II) fglrx(0): 	000c4cff0a3c640f131f640000000045
[    29.833] (II) fglrx(0): EDID vendor "LGD", prod id 927
[    29.833] (II) fglrx(0): Printing DDC gathered Modelines:
[    29.833] (II) fglrx(0): Modeline "1366x768"x0.0   76.30  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    29.833] (II) fglrx(0): Modeline "1366x768"x0.0   50.87  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Printing probed modes for output LVDS
[    29.833] (II) fglrx(0): Modeline "1366x768"x60.0   76.30  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    29.833] (II) fglrx(0): Modeline "1366x768"x40.0   50.87  1366 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Modeline "1280x768"x60.0   76.30  1280 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz e)
[    29.833] (II) fglrx(0): Modeline "1280x768"x40.0   50.87  1280 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Modeline "1280x720"x60.0   76.30  1280 1414 1446 1610  720 771 776 790 +hsync -vsync (47.4 kHz e)
[    29.833] (II) fglrx(0): Modeline "1280x720"x40.0   50.87  1280 1414 1446 1610  720 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Modeline "1024x768"x60.0   76.30  1024 1414 1446 1610  768 771 776 790 +hsync -vsync (47.4 kHz e)
[    29.833] (II) fglrx(0): Modeline "1024x768"x40.0   50.87  1024 1414 1446 1610  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Modeline "800x600"x60.0   76.30  800 1414 1446 1610  600 771 776 790 +hsync -vsync (47.4 kHz e)
[    29.833] (II) fglrx(0): Modeline "800x600"x40.0   50.87  800 1414 1446 1610  600 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): Modeline "640x480"x60.0   76.30  640 1414 1446 1610  480 771 776 790 +hsync -vsync (47.4 kHz e)
[    29.833] (II) fglrx(0): Modeline "640x480"x40.0   50.87  640 1414 1446 1610  480 771 776 790 +hsync -vsync (31.6 kHz e)
[    29.833] (II) fglrx(0): EDID for output DFP1
[    29.833] (II) fglrx(0): EDID for output CRT1
[    29.833] (II) fglrx(0): Output LVDS connected
[    29.833] (II) fglrx(0): Output DFP1 disconnected
[    29.833] (II) fglrx(0): Output CRT1 disconnected
[    29.833] (II) fglrx(0): Using exact sizes for initial modes
[    29.833] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    29.833] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.833] (II) fglrx(0): Display dimensions: (350, 190) mm
[    29.833] (II) fglrx(0): DPI set to (99, 102)
[    29.833] (II) fglrx(0): Adapter AMD Radeon(TM) R5 Graphics          has 2 configurable heads and 1 displays connected.
[    29.833] (==) fglrx(0):  PseudoColor visuals disabled
[    29.833] (II) Loading sub module "ramdac"
[    29.833] (II) LoadModule: "ramdac"
[    29.833] (II) Module "ramdac" already built-in
[    29.833] (==) fglrx(0): NoDRI = NO
[    29.833] (==) fglrx(0): Capabilities: 0x00000000
[    29.833] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    29.833] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    29.833] (==) fglrx(0): UseFastTLS=0
[    29.834] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    29.834] (II) UnloadModule: "radeon"
[    29.834] (II) Unloading radeon
[    29.834] (II) UnloadModule: "modesetting"
[    29.834] (II) Unloading modesetting
[    29.834] (II) UnloadModule: "fbdev"
[    29.834] (II) Unloading fbdev
[    29.834] (II) UnloadSubModule: "fbdevhw"
[    29.834] (II) Unloading fbdevhw
[    29.834] (II) UnloadModule: "vesa"
[    29.834] (II) Unloading vesa
[    29.834] (--) Depth 24 pixmap format is 32 bpp
[    29.834] Loading extension ATIFGLRXDRI
[    29.834] (II) fglrx(0): doing swlDriScreenInit
[    29.834] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    29.834] ukiDynamicMajor: found major device number 250
[    29.834] ukiDynamicMajor: found major device number 250
[    29.835] ukiDynamicMajor: found major device number 250
[    29.835] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    29.835] ukiOpenDevice: node name is /dev/ati/card0
[    29.835] ukiOpenDevice: open result is 12, (OK)
[    29.835] ukiOpenByBusid: ukiOpenMinor returns 12
[    29.835] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    29.835] (II) fglrx(0): [uki] DRM interface version 1.0
[    29.835] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[    29.835] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x14000
[    29.835] (II) fglrx(0): [uki] mapped SAREA 0x14000 to 0x7f0a56a3a000
[    29.835] (II) fglrx(0): [uki] framebuffer handle = 0x15000
[    29.835] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    29.835] (II) fglrx(0): swlDriScreenInit done
[    29.835] (II) fglrx(0): Kernel Module Version Information:
[    29.835] (II) fglrx(0):     Name: fglrx
[    29.835] (II) fglrx(0):     Version: 14.20.7
[    29.835] (II) fglrx(0):     Date: Aug 12 2014
[    29.835] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    29.835] (II) fglrx(0): Kernel Module version matches driver.
[    29.835] (II) fglrx(0): Kernel Module Build Time Information:
[    29.835] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-34-generic
[    29.835] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    29.835] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    29.835] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    29.835] (II) fglrx(0): [uki] register handle = 0x00016000
[    29.836] (II) fglrx(0): DRI initialization successfull
[    29.836] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01080000
```

I apologise fr dumping so much information here - like I say I have no idea what to make of this. If you need any more info, please let me know. Thanks.

---

### Post by Bashing-om on 2015-10-18
olly3; Hello; 

Curious set of circumstances. The file you provided is the primary one we would want to see. However, it does not report any errors that I can spot.

How did you install the proprietary (FGLRX) driver ? Maybe we are looking at the driver being broken in the update process to a new kernel ?
Is support for Dynamic Kernel Mode Setting provided ?
```

dkms status

```

Might be good to see the status of 'xorg"
```

dpkg -l xorg

```

What is contained in the FGLRX config file ?
```

cat /etc/X11/xorg.conf 

```

And what happens when we rebuild that file ?
```

sudo amdconfig --initial

```

After running the 'amdconfig' - REBOOT -; now ->
Is there a change in the ability to display the desktop ??

surely these results will point us in a direction of resolution.

[INDENT][INDENT]we just need to ask the system
[INDENT][INDENT][INDENT]the right question
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by olly3 on 2015-10-18
Hi, thanks for your response. 

The error I get upon boot up is 
```
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1)
Loading extension ATIFGLRXDRI
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/dgflrx_drv.so: unidentified symbol: GlxInitVisuals2D
```

I the get 
```
dkms status
fglrx, 14.201.1008, 3.13.0-24-generic, x86_64: installed
fglrx, 14.201.1008, 3.13.0-24-generic, x86_64: installed
virtualbox-guest, 4.3.10, 3.13.0-24-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)(WARNING! Diff between built and installed module!)
virtualbox-guest, 4.3.10, 3.13.0-34-generic, x86_64: installed
virtualbox-guest, 4.3.10, 3.16.1-031601-generic, x86_64: installed
```

```
dpkg -l xorg
dpkg-query: no packages found matching xorg
```

```
cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier    "aticonfig Layout"
    Screen    0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier    "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier    "aticonfig-Device[0]-0"
    Driver        "fglrx"
    BusID         "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier    "aticonfig-Screen[0]-0"
    Device       "aticonfig-Device[0]-0"
    Monitor      "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection  "Display"
           Viewport  0  0
           Depth      24
    EndSubSection
EndSection



```

At first xorg.conf seemed not to exist. I then ran sudo amdconfig --initial and got the output above

---

### Post by olly3 on 2015-10-18
I should say that I installed the proprietary driver over a year ago because the default one that came with the installation didn't allow me to play a certain video game. I would be more than happy to go back to the default driver though, if that would resolve these xorg issues.

---

### Post by Bashing-om on 2015-10-18
olly3; Yeikes !

I am totally mystified that 'xorg' is not installed. Or how that could possibly be ??

What happens if we RE-install 'xorg' ? As I consider 'xorg' to be a requirement for any DE .
```

sudo apt-get install --reinstall xorg

```
Looking here too to see if the package manager screams and hollers about dependency issues (xserver-xorg ?? ) .

Once more reboot to see the effect .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by olly3 on 2015-10-18
Hi, sorry for my late response - I installed xorg. It seemed to go well, the package manager did not complain. Upon rebooting my machine I still get the same error message that xorg is not working and that i should restart mdm once it is properly configured. I now get 
```
dpkg -l xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Unknown/Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                          Architecture                          Description
++==============-================-===================-===========
ii xorg                              1:7.7+1ubuntu8.1           amd64                                  X.Org X Window System 
```

---

### Post by Bashing-om on 2015-10-18
olly3; Well, well


Let's see if the system will give us any additional hints:
```

sudo dpkg-reconfigure xserver-xorg

```

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by olly3 on 2015-10-18
Unfortunately 
```
 sudo dpkg-reconfigure xserver-xorg 
```
returned nothing. 

At this point I'm tempted to resinstall linux, I really don't want to though - it took me ages to get everything set up the way I needed it.

---

### Post by Bashing-om on 2015-10-18
olly3; Hey. Like;

There are the pros and cons to (RE-)install . It is a nuclear solution, and a (RE-)install always works and is often times the faster.
Given time and effort we can isolate where the fault in starting the X layer lies. However, maybe a fumbling effort as many of us are not familiar with Mint.
Does this file exist ?
```

cat ~/.xsession-errors

```
Maybe it will give us a hint of what is failing.
Then there is removing the config files;
replacing the greeter
re-installing the desktop
and on and on and on /////

If one is interested, can be a good learning experience.

[INDENT][INDENT]I assert
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by olly3 on 2015-10-18
You know what, I'm just going to make sure everything is backed up and go for a reinstall. It will probably take me a while because, as I recall, when I first installed it I had problems with getting the grub menu to appear (dual booting with Windows 8 is a pain in the ****) and getting the Wifi driver working. I'll also have to reinstall all the software libraries I need. Its going to be a long night! I better put some coffee on....

---

### Post by Bashing-om on 2015-10-18
olly3; Welp;

! good thing about a (RE-)install .. will do better this time' knowing now what you do not want .

[INDENT][INDENT]a cloud
[INDENT][INDENT][INDENT]with a silver lining
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

