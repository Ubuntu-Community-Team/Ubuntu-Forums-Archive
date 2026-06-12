---
title: "No GUI after upgrade to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Nymn on 2011-04-29
I just upgraded my 10.10 machine to 11.04 and now it boots to the desktop, but in text only mode. Where did my GUI go?:(

---

### Post by manzdagratiano on 2011-04-30
Your system might be one of the ones where the default method of booting without an xorg.conf file does not yield optimum results. Log into the text mode with your username and password and issue:

```
sudo X -configure
```

and it will generate an xorg.conf file. Then reboot, and hopefully this time you will have your GUI.

---

### Post by Nymn on 2011-04-30
Okay, tried that. It gave me a "Number of created screens does not match number of detected devices. Configuration failed." error.  What does that mean?

---

### Post by manzdagratiano on 2011-04-30
From the following thread:

[https://bbs.archlinux.org/viewtopic.php?id=51637](https://bbs.archlinux.org/viewtopic.php?id=51637)

it seems like you may have the similar issue - your xorg.conf may be trying to load the fallback 'vesa' driver, and you may just need to comment it out. If that solution does not work for you, try posting the output of 'sudo X -configure' as well as your generated xorg.conf. I am sure this issue shall be easily resolved.

---

### Post by Nymn on 2011-04-30
Here's what I get from the X -configure command.

(EE) Can't load FireGL DRM library (libfglrxdrm.so)
(EE)Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to load module/driver vmwgfx
(EE) vmware: Unexpected failure while loading the "vmwlegacy" driver. Giving up.
(EE) Failed to load module "vmware" (a required submodule could not be loaded, 0)
(++) Using config file: "/home/user/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting
(EE) open /dev/fb0: No such file or directory
Number of created screens does not match number of dtected devices.
Configuration failed.
ddxSigGiveUp: Closing log


:confused:

---

### Post by Nymn on 2011-04-30
Here are some log and configuration files, thought they might help.

Xorg.0.log file:

```
[    21.212] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.212] X Protocol Version 11, Revision 0
[    21.212] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.212] Current Operating System: Linux dom-desktop 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    21.212] Kernel command line: root=UUID=5ca37436-5ab1-4889-96e3-9e8bc9a76425 ro quiet splash 
[    21.212] Build Date: 19 April 2011  03:33:17PM
[    21.212] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    21.212] Current version of pixman: 0.20.2
[    21.212] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.212] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.212] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 30 11:42:27 2011
[    21.212] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.212] (==) No Layout section.  Using the first Screen section.
[    21.212] (==) No screen section available. Using defaults.
[    21.212] (**) |-->Screen "Default Screen Section" (0)
[    21.212] (**) |   |-->Monitor "<default monitor>"
[    21.212] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.213] (==) Automatically adding devices
[    21.213] (==) Automatically enabling devices
[    21.213] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.213] 	Entry deleted from font path.
[    21.213] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.213] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.213] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.213] (II) Loader magic: 0x81ffde0
[    21.213] (II) Module ABI versions:
[    21.213] 	X.Org ANSI C Emulation: 0.4
[    21.213] 	X.Org Video Driver: 10.0
[    21.213] 	X.Org XInput driver : 12.3
[    21.213] 	X.Org Server Extension : 5.0
[    21.213] (--) PCI:*(0:1:0:0) 1002:954f:1682:2462 rev 0, Mem @ 0xd0000000/268435456, 0xfe9f0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    21.213] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.213] (II) LoadModule: "extmod"
[    21.214] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.214] (II) Module extmod: vendor="X.Org Foundation"
[    21.214] 	compiled for 1.10.1, module version = 1.0.0
[    21.214] 	Module class: X.Org Server Extension
[    21.214] 	ABI class: X.Org Server Extension, version 5.0
[    21.214] (II) Loading extension MIT-SCREEN-SAVER
[    21.214] (II) Loading extension XFree86-VidModeExtension
[    21.214] (II) Loading extension XFree86-DGA
[    21.214] (II) Loading extension DPMS
[    21.214] (II) Loading extension XVideo
[    21.214] (II) Loading extension XVideo-MotionCompensation
[    21.214] (II) Loading extension X-Resource
[    21.214] (II) LoadModule: "dbe"
[    21.214] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.214] (II) Module dbe: vendor="X.Org Foundation"
[    21.214] 	compiled for 1.10.1, module version = 1.0.0
[    21.214] 	Module class: X.Org Server Extension
[    21.214] 	ABI class: X.Org Server Extension, version 5.0
[    21.214] (II) Loading extension DOUBLE-BUFFER
[    21.214] (II) LoadModule: "glx"
[    21.214] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so
[    21.214] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    21.214] 	compiled for 6.9.0, module version = 1.0.0
[    21.214] (II) Loading extension GLX
[    21.215] (II) LoadModule: "record"
[    21.215] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.215] (II) Module record: vendor="X.Org Foundation"
[    21.215] 	compiled for 1.10.1, module version = 1.13.0
[    21.215] 	Module class: X.Org Server Extension
[    21.215] 	ABI class: X.Org Server Extension, version 5.0
[    21.215] (II) Loading extension RECORD
[    21.215] (II) LoadModule: "dri"
[    21.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.215] (II) Module dri: vendor="X.Org Foundation"
[    21.215] 	compiled for 1.10.1, module version = 1.0.0
[    21.215] 	ABI class: X.Org Server Extension, version 5.0
[    21.215] (II) Loading extension XFree86-DRI
[    21.215] (II) LoadModule: "dri2"
[    21.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.215] (II) Module dri2: vendor="X.Org Foundation"
[    21.215] 	compiled for 1.10.1, module version = 1.2.0
[    21.215] 	ABI class: X.Org Server Extension, version 5.0
[    21.215] (II) Loading extension DRI2
[    21.215] (==) Matched fglrx as autoconfigured driver 0
[    21.215] (==) Matched ati as autoconfigured driver 1
[    21.215] (==) Matched vesa as autoconfigured driver 2
[    21.215] (==) Matched fbdev as autoconfigured driver 3
[    21.215] (==) Assigned the driver to the xf86ConfigLayout
[    21.215] (II) LoadModule: "fglrx"
[    21.215] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    21.231] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    21.231] 	compiled for 1.4.99.906, module version = 8.84.60
[    21.231] 	Module class: X.Org Video Driver
[    21.231] (II) Loading sub module "fglrxdrm"
[    21.231] (II) LoadModule: "fglrxdrm"
[    21.231] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.231] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    21.231] 	compiled for 1.4.99.906, module version = 8.84.60
[    21.231] (II) LoadModule: "ati"
[    21.232] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.232] (II) Module ati: vendor="X.Org Foundation"
[    21.232] 	compiled for 1.10.0, module version = 6.14.0
[    21.232] 	Module class: X.Org Video Driver
[    21.232] 	ABI class: X.Org Video Driver, version 10.0
[    21.232] (II) LoadModule: "radeon"
[    21.232] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.232] (II) Module radeon: vendor="X.Org Foundation"
[    21.232] 	compiled for 1.10.0, module version = 6.14.0
[    21.232] 	Module class: X.Org Video Driver
[    21.232] 	ABI class: X.Org Video Driver, version 10.0
[    21.232] (II) LoadModule: "vesa"
[    21.232] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.232] (II) Module vesa: vendor="X.Org Foundation"
[    21.232] 	compiled for 1.10.0, module version = 2.3.0
[    21.232] 	Module class: X.Org Video Driver
[    21.232] 	ABI class: X.Org Video Driver, version 10.0
[    21.232] (II) LoadModule: "fbdev"
[    21.233] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.233] (II) Module fbdev: vendor="X.Org Foundation"
[    21.233] 	compiled for 1.10.0, module version = 0.4.2
[    21.233] 	ABI class: X.Org Video Driver, version 10.0
[    21.233] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    21.233] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    21.233] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    21.233] (II) RADEON: Driver for ATI Radeon chipsets:
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
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
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
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    21.237] (II) VESA: driver for VESA chipsets: vesa
[    21.237] (II) FBDEV: driver for framebuffer: fbdev
[    21.237] (--) using VT number 7

[    21.245] (WW) Falling back to old probe method for fglrx
[    21.252] (II) Loading PCS database from /etc/ati/amdpcsdb
[    21.253] (--) Assigning device section with no busID to primary device
[    21.253] (--) Chipset Supported AMD Graphics Processor (0x954F) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    21.253] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    21.253] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    21.253] (II) AMD Video driver is signed
[    21.253] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    21.253] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.253] (II) fglrx(0): pEnt->device->identifier=0x81ec828
[    21.253] (WW) Falling back to old probe method for vesa
[    21.253] (WW) Falling back to old probe method for fbdev
[    21.253] (II) Loading sub module "fbdevhw"
[    21.253] (II) LoadModule: "fbdevhw"
[    21.254] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.254] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.254] 	compiled for 1.10.1, module version = 0.0.2
[    21.254] 	ABI class: X.Org Video Driver, version 10.0
[    21.254] (EE) open /dev/fb0: No such file or directory
[    21.254] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    21.254] (II) Loading sub module "vgahw"
[    21.254] (II) LoadModule: "vgahw"
[    21.254] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    21.254] (II) Module vgahw: vendor="X.Org Foundation"
[    21.254] 	compiled for 1.10.1, module version = 0.1.0
[    21.254] 	ABI class: X.Org Video Driver, version 10.0
[    21.254] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.254] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    21.254] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.254] (==) fglrx(0): Default visual is TrueColor
[    21.254] (==) fglrx(0): RGB weight 888
[    21.254] (II) fglrx(0): Using 8 bits per RGB 
[    21.254] (==) fglrx(0): Buffer Tiling is ON
[    21.254] (II) Loading sub module "fglrxdrm"
[    21.254] (II) LoadModule: "fglrxdrm"
[    21.254] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.254] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    21.254] 	compiled for 1.4.99.906, module version = 8.84.60
[    21.256] ukiDynamicMajor: failed to open /proc/ati/major
[    21.256] ukiDynamicMajor: failed to open /proc/ati/major
[    21.256] (==) fglrx(0): NoAccel = NO
[    21.256] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    21.256] (--) fglrx(0): Chipset: "ATI Radeon HD 4300/4500 Series" (Chipset = 0x954f)
[    21.256] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x2462)
[    21.256] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    21.256] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    21.256] (--) fglrx(0): MMIO registers at 0xfe9f0000
[    21.256] (--) fglrx(0): I/O port at 0x0000c000
[    21.256] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    21.263] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    21.263] (EE) fglrx(0): ACPI: DRM connection failed
[    21.379] (II) Loading sub module "vbe"
[    21.379] (II) LoadModule: "vbe"
[    21.379] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.379] (II) Module vbe: vendor="X.Org Foundation"
[    21.379] 	compiled for 1.10.1, module version = 1.1.0
[    21.379] 	ABI class: X.Org Video Driver, version 10.0
[    21.379] (II) fglrx(0): VESA BIOS detected
[    21.379] (II) fglrx(0): VESA VBE Version 3.0
[    21.379] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    21.379] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    21.379] (II) fglrx(0): VESA VBE OEM Software Rev: 11.20
[    21.379] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    21.379] (II) fglrx(0): VESA VBE OEM Product: 0_113-ACXXXXX-100
[    21.379] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    21.406] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    21.406] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR2
[    21.406] (II) fglrx(0): PCIE card detected
[    21.406] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    21.406] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    21.406] (EE) fglrx(0): ACPI: DRM connection failed
[    21.406] (WW) fglrx(0): Hasn't establisted DRM connection
[    21.406] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    21.406] (WW) fglrx(0): No DRM connection for driver fglrx.
[    21.406] (II) fglrx(0): RandR 1.2 support is enabled!
[    21.406] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    21.406] (==) fglrx(0): Center Mode is disabled 
[    21.406] (II) Loading sub module "fb"
[    21.406] (II) LoadModule: "fb"
[    21.406] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.406] (II) Module fb: vendor="X.Org Foundation"
[    21.406] 	compiled for 1.10.1, module version = 1.0.0
[    21.406] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.406] (II) Loading sub module "ddc"
[    21.406] (II) LoadModule: "ddc"
[    21.406] (II) Module "ddc" already built-in
[    21.998] (II) fglrx(0): Output DFP1 has no monitor section
[    21.998] (II) fglrx(0): Output CRT1 has no monitor section
[    21.998] (II) fglrx(0): Output CRT2 has no monitor section
[    21.998] (II) fglrx(0): Output TV has no monitor section
[    21.998] (II) fglrx(0): Output CV has no monitor section
[    21.998] (II) Loading sub module "ddc"
[    21.998] (II) LoadModule: "ddc"
[    21.998] (II) Module "ddc" already built-in
[    21.998] (II) fglrx(0): Connected Display0: DFP1
[    21.998] (II) fglrx(0): Display0 EDID data ---------------------------
[    21.998] (II) fglrx(0): Manufacturer: ACI  Model: 24f2  Serial#: 16843009
[    21.998] (II) fglrx(0): Year: 2010  Week: 34
[    21.998] (II) fglrx(0): EDID Version: 1.3
[    21.998] (II) fglrx(0): Digital Display Input
[    21.998] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    21.998] (II) fglrx(0): Gamma: 2.20
[    21.998] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    21.998] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.998] (II) fglrx(0): Default color space is primary color space
[    21.998] (II) fglrx(0): First detailed timing is preferred mode
[    21.998] (II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
[    21.998] (II) fglrx(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
[    21.998] (II) fglrx(0): Supported established timings:
[    21.998] (II) fglrx(0): 720x400@70Hz
[    21.998] (II) fglrx(0): 640x480@60Hz
[    21.998] (II) fglrx(0): 640x480@67Hz
[    21.998] (II) fglrx(0): 640x480@72Hz
[    21.998] (II) fglrx(0): 640x480@75Hz
[    21.998] (II) fglrx(0): 800x600@56Hz
[    21.998] (II) fglrx(0): 800x600@60Hz
[    21.998] (II) fglrx(0): 800x600@72Hz
[    21.998] (II) fglrx(0): 800x600@75Hz
[    21.998] (II) fglrx(0): 832x624@75Hz
[    21.998] (II) fglrx(0): 1024x768@60Hz
[    21.998] (II) fglrx(0): 1024x768@70Hz
[    21.998] (II) fglrx(0): 1024x768@75Hz
[    21.998] (II) fglrx(0): 1280x1024@75Hz
[    21.998] (II) fglrx(0): Manufacturer's mask: 0
[    21.998] (II) fglrx(0): Supported standard timings:
[    21.998] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    21.998] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    21.998] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    21.998] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    21.998] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    21.998] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    21.998] (II) fglrx(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    21.998] (II) fglrx(0): Supported detailed timing:
[    21.998] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    21.998] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.998] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    21.998] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[    21.998] (II) fglrx(0): Monitor name: VW246
[    21.998] (II) fglrx(0): Serial No: A8LMQS023560
[    21.998] (II) fglrx(0): EDID (in hex):
[    21.998] (II) fglrx(0): 	00ffffffffffff000469f22401010101
[    21.998] (II) fglrx(0): 	2214010380351e78eec4f6a3574a9c23
[    21.998] (II) fglrx(0): 	114f54bfef00714f818081409500a940
[    21.998] (II) fglrx(0): 	b300d1c00101023a801871382d40582c
[    21.998] (II) fglrx(0): 	4500132b2100001e000000fd00384c1f
[    21.998] (II) fglrx(0): 	5311000a202020202020000000fc0056
[    21.998] (II) fglrx(0): 	573234360a20202020202020000000ff
[    21.998] (II) fglrx(0): 	0041384c4d51533032333536300a008b
[    21.998] (II) fglrx(0): End of Display0 EDID data --------------------
[    22.170] (II) fglrx(0): EDID for output DFP1
[    22.170] (II) fglrx(0): Manufacturer: ACI  Model: 24f2  Serial#: 16843009
[    22.170] (II) fglrx(0): Year: 2010  Week: 34
[    22.170] (II) fglrx(0): EDID Version: 1.3
[    22.170] (II) fglrx(0): Digital Display Input
[    22.170] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    22.170] (II) fglrx(0): Gamma: 2.20
[    22.170] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    22.170] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    22.170] (II) fglrx(0): Default color space is primary color space
[    22.170] (II) fglrx(0): First detailed timing is preferred mode
[    22.170] (II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
[    22.170] (II) fglrx(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
[    22.170] (II) fglrx(0): Supported established timings:
[    22.170] (II) fglrx(0): 720x400@70Hz
[    22.170] (II) fglrx(0): 640x480@60Hz
[    22.170] (II) fglrx(0): 640x480@67Hz
[    22.170] (II) fglrx(0): 640x480@72Hz
[    22.170] (II) fglrx(0): 640x480@75Hz
[    22.170] (II) fglrx(0): 800x600@56Hz
[    22.170] (II) fglrx(0): 800x600@60Hz
[    22.170] (II) fglrx(0): 800x600@72Hz
[    22.170] (II) fglrx(0): 800x600@75Hz
[    22.170] (II) fglrx(0): 832x624@75Hz
[    22.170] (II) fglrx(0): 1024x768@60Hz
[    22.170] (II) fglrx(0): 1024x768@70Hz
[    22.170] (II) fglrx(0): 1024x768@75Hz
[    22.170] (II) fglrx(0): 1280x1024@75Hz
[    22.170] (II) fglrx(0): Manufacturer's mask: 0
[    22.170] (II) fglrx(0): Supported standard timings:
[    22.170] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.170] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.170] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    22.170] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    22.170] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    22.170] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    22.170] (II) fglrx(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    22.170] (II) fglrx(0): Supported detailed timing:
[    22.170] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    22.170] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    22.170] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    22.170] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[    22.170] (II) fglrx(0): Monitor name: VW246
[    22.170] (II) fglrx(0): Serial No: A8LMQS023560
[    22.170] (II) fglrx(0): EDID (in hex):
[    22.170] (II) fglrx(0): 	00000000782830293a20537570706f72
[    22.170] (II) fglrx(0): 	7465642064657461696c65642074696d
[    22.170] (II) fglrx(0): 	696e673a0a0066726573683a20256920
[    22.170] (II) fglrx(0): 	20766964310000000000000078283029
[    22.170] (II) fglrx(0): 	3a204d6f6e69746f72206e616d653a20
[    22.170] (II) fglrx(0): 	25730a00000000000000000078283029
[    22.170] (II) fglrx(0): 	3a204669290000000000000078283029
[    22.170] (II) fglrx(0): 	3a20454449442028696e20686578293a
[    22.170] (II) fglrx(0): EDID vendor "ACI", prod id 9458
[    22.170] (II) fglrx(0): Using EDID range info for horizontal sync
[    22.170] (II) fglrx(0): Using EDID range info for vertical refresh
[    22.170] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.170] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    22.170] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.170] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.170] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.170] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.170] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    22.170] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.170] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.170] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    22.170] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.170] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.170] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.170] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.170] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.170] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.170] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.170] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.170] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    22.170] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    22.170] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    22.170] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    22.170] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    22.170] (II) fglrx(0): Printing probed modes for output DFP1
[    22.170] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    22.170] (II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync -vsync (62.1 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    22.171] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    22.171] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    22.171] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    22.171] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    22.171] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    22.171] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    22.171] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    22.171] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    22.171] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    22.171] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    22.171] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    22.171] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    22.171] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    22.171] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    22.171] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    22.171] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    22.171] (II) fglrx(0): EDID for output CRT1
[    22.171] (II) fglrx(0): EDID for output CRT2
[    22.171] (II) fglrx(0): EDID for output TV
[    22.171] (II) fglrx(0): EDID for output CV
[    22.171] (II) fglrx(0): Output DFP1 connected
[    22.171] (II) fglrx(0): Output CRT1 disconnected
[    22.171] (II) fglrx(0): Output CRT2 disconnected
[    22.171] (II) fglrx(0): Output TV disconnected
[    22.171] (II) fglrx(0): Output CV disconnected
[    22.171] (II) fglrx(0): Using exact sizes for initial modes
[    22.171] (II) fglrx(0): Output DFP1 using initial mode 1920x1080
[    22.171] (II) fglrx(0): Display dimensions: (530, 300) mm
[    22.171] (II) fglrx(0): DPI set to (92, 92)
[    22.171] (II) fglrx(0): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 1 displays connected.
[    22.171] (==) fglrx(0):  PseudoColor visuals disabled
[    22.171] (II) Loading sub module "ramdac"
[    22.171] (II) LoadModule: "ramdac"
[    22.171] (II) Module "ramdac" already built-in
[    22.171] (==) fglrx(0): NoDRI = NO
[    22.171] (==) fglrx(0): Capabilities: 0x00000000
[    22.171] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    22.171] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    22.171] (==) fglrx(0): UseFastTLS=0
[    22.171] (==) fglrx(0): BlockSignalsOnLock=1
[    22.171] (II) UnloadModule: "radeon"
[    22.171] (II) Unloading radeon
[    22.171] (II) UnloadModule: "vesa"
[    22.171] (II) Unloading vesa
[    22.171] (II) UnloadModule: "fbdev"
[    22.171] (II) Unloading fbdev
[    22.171] (II) UnloadModule: "fbdevhw"
[    22.171] (II) Unloading fbdevhw
[    22.171] (--) Depth 24 pixmap format is 32 bpp
[    22.171] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    22.171] (WW) fglrx(0): ***********************************************************
[    22.171] (WW) fglrx(0): * DRI initialization failed                               *
[    22.171] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    22.171] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    22.171] (WW) fglrx(0): ***********************************************************
[    22.171] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[    22.197] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
[    22.197] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[    22.197] (II) fglrx(0): Largest offscreen area available: 1920 x 6271
[    22.197] (==) fglrx(0): Backing store disabled
[    22.197] (II) Loading extension FGLRXEXTENSION
[    22.197] (==) fglrx(0): DPMS enabled
[    22.198] (II) fglrx(0): Initialized in-driver Xinerama extension
[    22.198] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    22.198] (II) LoadModule: "glesx"
[    22.198] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    22.199] (II) Module glesx: vendor="X.Org Foundation"
[    22.199] 	compiled for 1.4.99.906, module version = 1.0.0
[    22.199] (II) Loading extension GLESX
[    22.199] (II) fglrx(0): GLESX enableFlags = 512
[    22.199] (II) LoadModule: "amdxmm"
[    22.199] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    22.199] (II) Module amdxmm: vendor="X.Org Foundation"
[    22.199] 	compiled for 1.4.99.906, module version = 2.0.0
[    22.199] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[    22.199] (EE) fglrx(0): XMM failed to initialize
[    22.199] (WW) fglrx(0): No XV video playback available
[    22.199] (II) fglrx(0): Enable composite support successfully
[    22.199] (==) fglrx(0): Silken mouse enabled
[    22.199] (==) fglrx(0): Using HW cursor of display infrastructure!
[    22.199] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    22.199] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    22.199] (II) fglrx(0): Cannot set TV horizontal size.
[    22.199] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    22.199] (II) fglrx(0): Cannot set TV horizontal position.
[    22.200] (II) fglrx(0): Cannot set TV vertical position.
[    22.308] (--) RandR disabled
[    22.308] (II) Initializing built-in extension Generic Event Extension
[    22.308] (II) Initializing built-in extension SHAPE
[    22.308] (II) Initializing built-in extension MIT-SHM
[    22.308] (II) Initializing built-in extension XInputExtension
[    22.308] (II) Initializing built-in extension XTEST
[    22.308] (II) Initializing built-in extension BIG-REQUESTS
[    22.308] (II) Initializing built-in extension SYNC
[    22.308] (II) Initializing built-in extension XKEYBOARD
[    22.308] (II) Initializing built-in extension XC-MISC
[    22.308] (II) Initializing built-in extension SECURITY
[    22.308] (II) Initializing built-in extension XINERAMA
[    22.308] (II) Initializing built-in extension XFIXES
[    22.308] (II) Initializing built-in extension RENDER
[    22.308] (II) Initializing built-in extension RANDR
[    22.308] (II) Initializing built-in extension COMPOSITE
[    22.308] (II) Initializing built-in extension DAMAGE
[    22.308] (II) Initializing built-in extension GESTURE
[    22.310] 
Backtrace:
[    22.311] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[    22.311] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[    22.311] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb779440c]
[    22.311] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0x30) [0xb68d0120]
[    22.311] 4: /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so (0xb72cc000+0xfc2c) [0xb72dbc2c]
[    22.311] 5: /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so (0xb72cc000+0x121fa) [0xb72de1fa]
[    22.311] 6: /usr/lib/xorg/extra-modules/modules/extensions/fglrx/libglx.so (0xb72cc000+0x118c7) [0xb72dd8c7]
[    22.311] 7: /usr/bin/X (InitExtensions+0x9d) [0x80d057d]
[    22.311] 8: /usr/bin/X (0x8048000+0x1a692) [0x8062692]
[    22.311] 9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb74a8e37]
[    22.311] 10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[    22.311] Segmentation fault at address 0x50
[    22.311] 
Caught signal 11 (Segmentation fault). Server aborting
[    22.311] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    22.311] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    22.311] 
[    22.780] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[    22.787]  ddxSigGiveUp: Closing log
```


xorg.conf file:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

xorg.conf.new file:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "extmod"
	Load  "dri"
	Load  "glx"
	Load  "record"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Nymn on 2011-04-30
I clicked on System>Administration>Additional Drivers and it says the proprietary drivers aren't activated. Would that help or make it worse? It's an ATI/AMD FGLRX driver.

---

