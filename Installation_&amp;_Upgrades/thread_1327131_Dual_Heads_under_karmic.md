---
title: "Dual Heads under karmic"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by nexes128 on 2009-11-15
Hello All, I just upgraded from 8.04 LTS to karmic and I am having some issues getting dual heads up (I did have them working under 8.04), right now my two monitors are working and I can drag and drop, etc ...

The Problems

[LIST=1]
[*] Anytime I right click on the second monitor the context menu pops up on the primary monitor
[*]When booting/loging in the ubuntu logo/progress bar is covered by a grey box (starting from the upper right hand corner and extending down just past the progress bar) (I can still see the logo somewhat as the box is semi transparent)
[*]Not really related to dual heads but I have WinXp on /dev/sda1 (linux on /dev/sdb1) and grub didn't detect and add XP, then
when I go under /boot/grub/grub.cfg it appears to have been replaced by a perl script (I was able to find out that /etc/defaults/grub to turn the grub boot menu back on but XP is not listed) and menu.lst is missing, does anyone know what happened to my real config file so I can manually add the WinXP partition?
[/LIST]

Alright now for the info on my setup

Video Card: ATI All-In-Wonder 2006 AGP Edition (Essentially its an ATI Radeon 9600)
Driver: radeon using xrandr (my card is no longer supported by ATI so I can not use their driver like I did under 8, the older version doesnt appear to run under karmic as well just my luck lol)
Monitor 1 (VGA-1): 1280x1024@75Hz
Monitor 2 (VGA-0): 1280x1024@60Hz

Here's my xorg.conf
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"radeon"
	Busid		"PCI:1:0:0"
	Option		"monitor-VGA-1" "monLeft"
	Option		"monitor-VGA-0" "monRight"
EndSection

Section "Monitor"
	Identifier	"monLeft"
	Option		"PreferredMode" "1280x1024"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monRight"
	Option		"PreferredMode" "1280x1024"
	Option		"RightOf" "monLeft"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"monLeft"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"
		Virtual 2560 1024	
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen "Default Screen"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

Script for xrandr
```

#/bin/bash
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00
xrandr --output VGA-0 --right-of VGA-1 --mode 1280x1024_60.00

```

Xorg.0.log output 
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=d32f6540-f202-408e-86f8-9eee94bfc502 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 15 04:34:10 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "monLeft"
(**) |   |-->Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:4150:1002:4722 ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xe0000000/268435456, 0xfe5f0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
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
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
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
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000fe5f0000
(II) RADEON(0): MMIO registers at 0x00000000fe5f0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 19575, sclk: 324.000000, mclk: 195.750000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=19575
(II) RADEON(0): Output VGA-1 using monitor section monLeft
(**) RADEON(0): Option "PreferredMode" "1280x1024"
(II) RADEON(0): I2C bus "VGA-1" initialized.
(II) RADEON(0): Output VGA-0 using monitor section monRight
(**) RADEON(0): Option "PreferredMode" "1280x1024"
(**) RADEON(0): Option "RightOf" "monLeft"
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
  XRANDR name: VGA-1
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: VGA-0
  Connector: VGA
  CRT2: INTERNAL_DAC2
  DDC reg: 0x6c
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-1:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-1:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
finished output detect: 0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-1 connected
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output VGA-1 using initial mode 1280x1024
(**) RADEON(0): Display dimensions: (360, 270) mm
(**) RADEON(0): DPI set to (180, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): MM_TABLE: 01-0c-16-19-06-00-33-66-02-05-06-00-00-07
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
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
(II) RADEON(0): RADEONScreenInit e0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable primary dac
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (2560,8191)
(II) RADEON(0): Reserved area from (0,1024) to (2560,1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7165
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00a05000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00a0a000
(II) RADEON(0): Largest offscreen area available: 2560 x 7161
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): Using R200 i2c bus access method
(II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
(II) Loading sub module "fi1236"
(II) LoadModule: "fi1236"
(II) Loading /usr/lib/xorg/modules/multimedia//fi1236_drv.so
(II) Module fi1236: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
(II) RADEON(0): Detected UNKNOWN-22 device at 0xc6
(II) Loading sub module "uda1380"
(II) LoadModule: "uda1380"
(II) Loading /usr/lib/xorg/modules/multimedia//uda1380_drv.so
(II) Module uda1380: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "msp3430"
(II) LoadModule: "msp3430"
(II) Loading /usr/lib/xorg/modules/multimedia//msp3430_drv.so
(II) Module msp3430: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): No response from device 0 on VIP bus
(II) RADEON(0): No response from device 1 on VIP bus
(II) RADEON(0): No response from device 2 on VIP bus
(II) RADEON(0): No response from device 3 on VIP bus
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable TVDAC
disable TV
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 135000000
best_freq: 135000000
best_feedback_div: 20
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
disable TVDAC
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "PreferredMode" is not used
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) GLX error: Can not get required symbols.
(II) RADEON(0): Setting screen physical size to 352 x 264
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
(II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
(II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
(**) Logitech Logitech BT Mini-Receiver: (accel) filter chain progression: 2.00
(**) Logitech Logitech BT Mini-Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech Logitech BT Mini-Receiver: (accel) set acceleration profile 0
(II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event4"
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event3"
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) set acceleration profile 0
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hAright now for the problems

1) Anytime I right click on the second monitor the context menu pops up on the primary
2) When booting/loging in the ubuntu logo/progress bar is covered by a grey box (I can still see the logo somewhat)
3) Not really related to dual heads but I have WinXp on /dev/sda1 (lin on /dev/sdb1) and grub didn't detect and add it
when I go under /boot/grub/grub.cfg it appears to have been replaced by a perl script (I was able to find out that /etc/defaults/grub
is where I go to turn the grub menu back on), does anyone know what happened to my real config file so I can manually add the WinXP part?
size: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-1
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1792x1344"x0.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.6 kHz)
(II) RADEON(0): Output: VGA-1, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-1 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 2d  Serial#: 1095643449
(II) RADEON(0): Year: 2003  Week: 39
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.47
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) RADEON(0): #5: hsize: 1792  vsize 1344  refresh: 60  vid: 16577
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 190 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HMCW904566
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d2d0039314e41
(II) RADEON(0): 	270d010368241b2f2bbbb9a352469824
(II) RADEON(0): 	0f484ca403003140315945596159818f
(II) RADEON(0): 	c14001010101bc34009851002a401090
(II) RADEON(0): 	130060081100001e000000fd0032a01e
(II) RADEON(0): 	5513000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00484d43573930343536360a20200060
(II) RADEON(0): EDID vendor "SAM", prod id 45
(II) RADEON(0): Not using mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1080" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-1
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) RADEON(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable primary dac
disable TVDAC
init memmap
init common
init crtc2
init pll2
freq: 109000000
best_freq: 109000000
best_feedback_div: 109
best_frac_feedback_div: 0
best_ref_div: 9
best_post_div: 3
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
set TVDAC
enable primary dac
enable TVDAC

```


I would greatly appreciate any help you can give

---

### Post by nexes128 on 2009-11-15
*bump*

---

### Post by nexes128 on 2009-11-16
I take it noone has any ideas?

---

### Post by arpanaut on 2009-11-16
Can't help on the dual head probs.

But about the windows not being recognized/detected, this seems to be common on the first writing of grub.cfg...

Usually a simple:

```
sudo update-grub
```

solves the problem

For reference: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

