---
title: "AIGLX: Calling driver entry point failed - Radeon"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by vinella on 2011-05-28
Upgraded to 11.04 - radeon driver gives error above in log below - screen works (software rasterizer) for a while and then eventually freezes.

fbdev driver works.

Installed very latest software updates available on net.

Would appreciate help getting my hardware acceleration back.

-------------------------------------------------------------
[    20.483] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    20.483] X Protocol Version 11, Revision 0
[    20.483] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    20.483] Current Operating System: Linux Desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    20.483] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=7e73a15f-59e1-4f87-ab7a-2bf1734614c9 ro splash quiet splash pcie_aspm=off vt.handoff=7
[    20.484] Build Date: 30 April 2011  10:08:56PM
[    20.484] xorg-server 2:1.10.1+git20110429+server-1.10-branch.b4455b11-0ubuntu0sarvatt (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.484] Current version of pixman: 0.21.8
[    20.484] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    20.484] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.484] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May 29 09:16:26 2011
[    20.485] (==) Using config file: "/etc/X11/xorg.conf"
[    20.485] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.486] (==) No Layout section.  Using the first Screen section.
[    20.486] (**) |-->Screen "Default Screen" (0)
[    20.486] (**) |   |-->Monitor "Samsung 213T"
[    20.486] (**) |   |-->Device "Configured Video Device"
[    20.486] (==) Automatically adding devices
[    20.486] (==) Automatically enabling devices
[    20.487] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.487] 	Entry deleted from font path.
[    20.487] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.487] 	Entry deleted from font path.
[    20.487] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.487] 	Entry deleted from font path.
[    20.487] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.487] 	Entry deleted from font path.
[    20.487] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.487] 	Entry deleted from font path.
[    20.487] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.487] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.487] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.487] (II) Loader magic: 0x8200a80
[    20.487] (II) Module ABI versions:
[    20.487] 	X.Org ANSI C Emulation: 0.4
[    20.487] 	X.Org Video Driver: 10.0
[    20.487] 	X.Org XInput driver : 12.3
[    20.487] 	X.Org Server Extension : 5.0
[    20.489] (--) PCI:*(0:1:0:0) 1002:4242:1002:02aa rev 0, Mem @ 0xf0000000/134217728, 0xff800000/131072, 0xff840000/65536, I/O @ 0x0000a800/256, BIOS @ 0x????????/131072
[    20.490] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    20.490] (II) LoadModule: "extmod"
[    20.512] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.512] (II) Module extmod: vendor="X.Org Foundation"
[    20.513] 	compiled for 1.10.1, module version = 1.0.0
[    20.513] 	Module class: X.Org Server Extension
[    20.513] 	ABI class: X.Org Server Extension, version 5.0
[    20.513] (II) Loading extension MIT-SCREEN-SAVER
[    20.513] (II) Loading extension XFree86-VidModeExtension
[    20.513] (II) Loading extension XFree86-DGA
[    20.513] (II) Loading extension DPMS
[    20.513] (II) Loading extension XVideo
[    20.513] (II) Loading extension XVideo-MotionCompensation
[    20.513] (II) Loading extension X-Resource
[    20.513] (II) LoadModule: "dbe"
[    20.514] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.514] (II) Module dbe: vendor="X.Org Foundation"
[    20.514] 	compiled for 1.10.1, module version = 1.0.0
[    20.514] 	Module class: X.Org Server Extension
[    20.514] 	ABI class: X.Org Server Extension, version 5.0
[    20.514] (II) Loading extension DOUBLE-BUFFER
[    20.514] (II) LoadModule: "glx"
[    20.515] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.515] (II) Module glx: vendor="X.Org Foundation"
[    20.515] 	compiled for 1.10.1, module version = 1.0.0
[    20.515] 	ABI class: X.Org Server Extension, version 5.0
[    20.515] (==) AIGLX enabled
[    20.515] (II) Loading extension GLX
[    20.515] (II) LoadModule: "record"
[    20.516] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.516] (II) Module record: vendor="X.Org Foundation"
[    20.517] 	compiled for 1.10.1, module version = 1.13.0
[    20.517] 	Module class: X.Org Server Extension
[    20.517] 	ABI class: X.Org Server Extension, version 5.0
[    20.517] (II) Loading extension RECORD
[    20.517] (II) LoadModule: "dri"
[    20.517] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.518] (II) Module dri: vendor="X.Org Foundation"
[    20.518] 	compiled for 1.10.1, module version = 1.0.0
[    20.518] 	ABI class: X.Org Server Extension, version 5.0
[    20.518] (II) Loading extension XFree86-DRI
[    20.518] (II) LoadModule: "dri2"
[    20.519] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.519] (II) Module dri2: vendor="X.Org Foundation"
[    20.519] 	compiled for 1.10.1, module version = 1.2.0
[    20.519] 	ABI class: X.Org Server Extension, version 5.0
[    20.519] (II) Loading extension DRI2
[    20.519] (II) LoadModule: "radeon"
[    20.520] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    20.571] (II) Module radeon: vendor="X.Org Foundation"
[    20.571] 	compiled for 1.10.1, module version = 6.14.99
[    20.571] 	Module class: X.Org Video Driver
[    20.571] 	ABI class: X.Org Video Driver, version 10.0
[    20.578] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
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
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    20.615] (++) using VT number 7

[    20.616] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    20.616] (II) [KMS] Kernel modesetting enabled.
[    20.616] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    20.616] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    20.616] (==) RADEON(0): Default visual is TrueColor
[    20.617] (==) RADEON(0): RGB weight 888
[    20.617] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    20.617] (--) RADEON(0): Chipset: "ATI Radeon 8500 AIW BB (AGP)" (ChipID = 0x4242)
[    20.617] (II) RADEON(0): AGP card detected
[    20.617] drmOpenDevice: node name is /dev/dri/card0
[    20.617] drmOpenDevice: open result is 8, (OK)
[    20.617] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    20.617] drmOpenDevice: node name is /dev/dri/card0
[    20.617] drmOpenDevice: open result is 8, (OK)
[    20.617] drmOpenByBusid: drmOpenMinor returns 8
[    20.617] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    20.617] (II) Loading sub module "exa"
[    20.617] (II) LoadModule: "exa"
[    20.627] (II) Loading /usr/lib/xorg/modules/libexa.so
[    20.644] (II) Module exa: vendor="X.Org Foundation"
[    20.644] 	compiled for 1.10.1, module version = 2.5.0
[    20.644] 	ABI class: X.Org Video Driver, version 10.0
[    20.644] (II) RADEON(0): KMS Color Tiling: disabled
[    20.644] (II) RADEON(0): KMS Pageflipping: enabled
[    20.644] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    20.831] (II) RADEON(0): Output DVI-0 using monitor section Samsung 213T
[    20.977] (II) RADEON(0): EDID for output DVI-0
[    20.977] (II) RADEON(0): Manufacturer: SAM  Model: 91  Serial#: 1312961073
[    20.977] (II) RADEON(0): Year: 2004  Week: 2
[    20.977] (II) RADEON(0): EDID Version: 1.3
[    20.977] (II) RADEON(0): Digital Display Input
[    20.977] (II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 32
[    20.978] (II) RADEON(0): Gamma: 2.60
[    20.978] (II) RADEON(0): DPMS capabilities: Off
[    20.978] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.978] (II) RADEON(0): First detailed timing is preferred mode
[    20.978] (II) RADEON(0): redX: 0.632 redY: 0.353   greenX: 0.293 greenY: 0.590
[    20.978] (II) RADEON(0): blueX: 0.140 blueY: 0.090   whiteX: 0.310 whiteY: 0.340
[    20.978] (II) RADEON(0): Supported established timings:
[    20.978] (II) RADEON(0): 720x400@70Hz
[    20.978] (II) RADEON(0): 640x480@60Hz
[    20.978] (II) RADEON(0): 640x480@67Hz
[    20.978] (II) RADEON(0): 640x480@72Hz
[    20.978] (II) RADEON(0): 640x480@75Hz
[    20.978] (II) RADEON(0): 800x600@56Hz
[    20.978] (II) RADEON(0): 800x600@60Hz
[    20.978] (II) RADEON(0): 800x600@72Hz
[    20.978] (II) RADEON(0): 800x600@75Hz
[    20.978] (II) RADEON(0): 832x624@75Hz
[    20.978] (II) RADEON(0): 1024x768@60Hz
[    20.978] (II) RADEON(0): 1024x768@70Hz
[    20.978] (II) RADEON(0): 1024x768@75Hz
[    20.978] (II) RADEON(0): 1280x1024@75Hz
[    20.978] (II) RADEON(0): 1152x864@75Hz
[    20.978] (II) RADEON(0): Manufacturer's mask: 0
[    20.978] (II) RADEON(0): Supported standard timings:
[    20.978] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    20.978] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.978] (II) RADEON(0): Supported detailed timing:
[    20.978] (II) RADEON(0): clock: 130.4 MHz   Image Size:  432 x 324 mm
[    20.978] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[    20.978] (II) RADEON(0): v_active: 1200  v_sync: 1202  v_sync_end 1206 v_blanking: 1235 v_border: 0
[    20.979] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    20.979] (II) RADEON(0): Monitor name: SyncMaster
[    20.979] (II) RADEON(0): Serial No: H4JX101519
[    20.979] (II) RADEON(0): EDID (in hex):
[    20.979] (II) RADEON(0): 	00ffffffffffff004c2d91003132424e
[    20.979] (II) RADEON(0): 	020e0103802b20a02ad0c4a15a4b9723
[    20.979] (II) RADEON(0): 	174f57bfef80a9408180010101010101
[    20.979] (II) RADEON(0): 	010101010101ed3240a060b023403020
[    20.979] (II) RADEON(0): 	2400b0441100001a000000fd00384b1e
[    20.979] (II) RADEON(0): 	510e000a202020202020000000fc0053
[    20.979] (II) RADEON(0): 	796e634d61737465720a2020000000ff
[    20.979] (II) RADEON(0): 	0048344a583130313531390a20200038
[    20.979] (II) RADEON(0): EDID vendor "SAM", prod id 145
[    20.979] (II) RADEON(0): Using hsync ranges from config file
[    20.979] (II) RADEON(0): Using vrefresh ranges from config file
[    20.979] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.979] (II) RADEON(0): Modeline "1600x1200"x0.0  130.37  1600 1648 1680 1760  1200 1202 1206 1235 +hsync -vsync (74.1 kHz)
[    20.979] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.979] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.979] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.979] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    20.979] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    20.979] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.979] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.979] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.979] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.993] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    20.993] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.993] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    20.993] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.993] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    20.993] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.993] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    20.993] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.993] (II) RADEON(0): Printing probed modes for output DVI-0
[    20.993] (II) RADEON(0): Modeline "1600x1200"x60.0  130.37  1600 1648 1680 1760  1200 1202 1206 1235 +hsync -vsync (74.1 kHz)
[    20.994] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.994] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.994] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.994] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    20.994] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    20.994] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.994] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    20.994] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    20.994] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.994] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.994] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.994] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    20.994] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.994] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    20.994] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.994] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.994] (II) RADEON(0): Output DVI-0 connected
[    20.994] (II) RADEON(0): Using exact sizes for initial modes
[    20.995] (II) RADEON(0): Output DVI-0 using initial mode 1600x1200
[    20.995] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.995] (II) RADEON(0): mem size init: gart size :fdff000 vram size: s:4000000 visible:386d000
[    20.995] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    20.995] (**) RADEON(0): Display dimensions: (430, 320) mm
[    20.995] (**) RADEON(0): DPI set to (94, 95)
[    20.995] (II) Loading sub module "fb"
[    20.995] (II) LoadModule: "fb"
[    21.000] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.000] (II) Module fb: vendor="X.Org Foundation"
[    21.000] 	compiled for 1.10.1, module version = 1.0.0
[    21.000] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.000] (II) Loading sub module "ramdac"
[    21.000] (II) LoadModule: "ramdac"
[    21.000] (II) Module "ramdac" already built-in
[    21.000] (--) Depth 24 pixmap format is 32 bpp
[    21.001] (II) RADEON(0): [DRI2] Setup complete
[    21.001] (II) RADEON(0): [DRI2]   DRI driver: r200
[    21.001] (II) RADEON(0): Front buffer size: 7500K
[    21.001] (II) RADEON(0): VRAM usage limit set to 45252K
[    21.001] (==) RADEON(0): Backing store disabled
[    21.001] (II) RADEON(0): Direct rendering enabled
[    21.017] (II) RADEON(0): Render acceleration enabled for R200 type cards.
[    21.017] (II) RADEON(0): Setting EXA maxPitchBytes
[    21.017] (II) EXA(0): Driver allocated offscreen pixmaps
[    21.017] (II) EXA(0): Driver registered support for the following operations:
[    21.017] (II)         Solid
[    21.017] (II)         Copy
[    21.017] (II)         Composite (RENDER acceleration)
[    21.017] (II)         UploadToScreen
[    21.017] (II)         DownloadFromScreen
[    21.023] (II) RADEON(0): Acceleration enabled
[    21.023] (==) RADEON(0): DPMS enabled
[    21.023] (==) RADEON(0): Silken mouse enabled
[    21.030] (II) RADEON(0): Set up textured video
[    21.030] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.030] (--) RandR disabled
[    21.031] (II) Initializing built-in extension Generic Event Extension
[    21.031] (II) Initializing built-in extension SHAPE
[    21.031] (II) Initializing built-in extension MIT-SHM
[    21.031] (II) Initializing built-in extension XInputExtension
[    21.031] (II) Initializing built-in extension XTEST
[    21.031] (II) Initializing built-in extension BIG-REQUESTS
[    21.031] (II) Initializing built-in extension SYNC
[    21.031] (II) Initializing built-in extension XKEYBOARD
[    21.031] (II) Initializing built-in extension XC-MISC
[    21.031] (II) Initializing built-in extension SECURITY
[    21.031] (II) Initializing built-in extension XINERAMA
[    21.031] (II) Initializing built-in extension XFIXES
[    21.031] (II) Initializing built-in extension RENDER
[    21.031] (II) Initializing built-in extension RANDR
[    21.031] (II) Initializing built-in extension COMPOSITE
[    21.031] (II) Initializing built-in extension DAMAGE
[    21.031] (II) Initializing built-in extension GESTURE
[    21.073] (II) AIGLX: Trying DRI driver /usr/lib/dri/r200_dri.so
[    21.118] (II) AIGLX: Calling driver entry point failed
[    21.118] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/r200_dri.so
[    21.144] (II) AIGLX: Calling driver entry point failed
[    21.144] (II) AIGLX: Trying DRI driver /usr/lib32/dri/r200_dri.so
[    21.144] (II) AIGLX: dlopen of /usr/lib32/dri/r200_dri.so failed (/usr/lib32/dri/r200_dri.so: cannot open shared object file: No such file or directory)
[    21.144] (II) AIGLX: Trying DRI driver /usr/lib32/dri-alternates/r200_dri.so
[    21.144] (II) AIGLX: dlopen of /usr/lib32/dri-alternates/r200_dri.so failed (/usr/lib32/dri-alternates/r200_dri.so: cannot open shared object file: No such file or directory)
[    21.144] (EE) AIGLX: reverting to software rendering
[    21.144] (II) AIGLX: Screen 0 is not DRI capable
[    21.144] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    21.145] (II) AIGLX: Loaded and initialized swrast
[    21.145] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    21.147] (II) RADEON(0): Setting screen physical size to 423 x 317
[    21.199] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.249] (II) config/udev: Adding input device Power Button (/dev/input/event1)<br>

---

### Post by vinella on 2011-06-10
Kept up with all the updates and now the fbdev driver freezes occasionally :(

Radeon/R200 driver still regularly freezes although now with latest updates it doesn't fall back to software rasterizer.

---

### Post by wildmanne39 on 2011-06-10
> **vinella said:**
> Kept up with all the updates and now the fbdev driver freezes occasionally :(

Radeon/R200 driver still regularly freezes although now with latest updates it doesn't fall back to software rasterizer.
Hi, do you have rendering enabled in compiz or manager for your video card? that is what it looks like if so you might try unchecking rendering and see if that helps.

---

### Post by vinella on 2011-06-10
> **wildmanne39 said:**
> 
Hi, do you have rendering enabled in compiz

Hi - I don't see any option in compiz to do this ???

---

### Post by wildmanne39 on 2011-06-10
> **vinella said:**
> Hi - I don't see any option in compiz to do this ???

Hi, the place I have it is in skydome settings in the cube, if you do not have that set up then you may not have it in compiz, I also have it in my manager for my video card again, I do not know if your card has a separate manager, with the direct rendering setting.

---

