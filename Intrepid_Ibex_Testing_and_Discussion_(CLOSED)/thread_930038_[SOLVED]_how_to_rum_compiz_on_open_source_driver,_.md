---
title: "[SOLVED] ?how to rum compiz on open source driver, link says it works"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-09-25
[http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1)

anyone know how to make that work?
I am running an ATI x1300 with Ibex. That means I have 7.4 xorg and 1.5 xserver and 7.2 mesa, so it should be possible.

---

### Post by RAOF on 2008-09-25
If the various branches that implement that support have been merged and released (particularly mesa 7.2), then it should Just Work.  There's almost never any setup - either it works or it doesn't, and no amount of non-coding will make it work ;).

If you'd expect this to work then I'd guess that you got hit by the packaging bug which installed the nvidia-glx-173 drivers at some point in the past, although I'd need to check your Xorg.0.log to be sure.

---

### Post by sdowney717 on 2008-09-26
Ok, I am running Ibex which has all these up to date versions included.
I have an ATI x1300.
I did have an nvidia in for a little while.
I could not get fglrx working since xorg 7.4 and fglrx are incompatible.

```


X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux scott-desktop 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686
Build Date: 24 September 2008  06:28:32PM
xorg-server 2:1.5.1-1ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 25 17:48:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "glx" (module requirement mismatch, 0)
finished output detect: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
in RADEONProbeOutputModes
Dac detection success
after xf86InitialConfiguration
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1792x1344 - 2448 1394 6
freq: 204800000
best_freq: 204800000
best_feedback_div: 1024
best_ref_div: 27
best_post_div: 5
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
in RADEONProbeOutputModes
Dac detection success
AUDIT: Thu Sep 25 17:48:53 2008: 7451 X: client 4 rejected from local host ( uid=0 gid=0 pid=7859 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7914 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7915 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7916 )
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x1024 - 1688 1066 5
freq: 108000000
best_freq: 108000000
best_feedback_div: 48
best_ref_div: 2
best_post_div: 6
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success


```


```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"        
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

``````

```

---

### Post by sdowney717 on 2008-09-26
here is what i have right now as of this moment

```

(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux scott-desktop 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686
Build Date: 24 September 2008  06:28:32PM
xorg-server 2:1.5.1-1ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 25 17:48:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) Option "AIGLX" "true"
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
(**) Extension "Composite" is enabled
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

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] rev 0, Mem @ 0xe0000000/0, 0xf0400000/0, I/O @ 0x00002000/0, BIOS @ 0x????????/131072
(--) PCI: (0@1:0:1) ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary) rev 0, Mem @ 0xf0410000/0
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
	compiled for 1.5.1, module version = 1.0.0
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
	compiled for 1.5.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.9.0
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
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
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
(II) RADEON(0): MMIO registers at 0x00000000f0400000: size 64KB
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
	compiled for 1.5.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1300/X1550" (ChipID = 0x7142)
(WW) RADEON(0): R500 support is under development. Please report any issues to xorg-driver-ati@lists.x.org
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x030b
	IOBaseAddress: 0x2000
	Filename: SR20030.002 
	BIOS Bootup Message: 

PCP RV515Pro Rialto 256mb Infineon DDR2 BIOS 600e/400m Channel AB           


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 600000
(II) RADEON(0): Default Memory Clock: 405000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=13 min=64800 max=110000; xclk=40000
(II) RADEON(0): Skipping TV-Out
(II) RADEON(0): Skipping Component Video
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x7e40, DACType-1, TMDSType-0, ConnectorType-1, hpd_mask-0x0
(II) RADEON(0): Port9: DDCType-0x7e50, DACType-2, TMDSType-3, ConnectorType-2, hpd_mask-0x100
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): TMDS PLL from BIOS: 16500 a0115
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- LVTMA
 DDC Type  -- 0x7e50
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using fuzzy aspect match for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1792x1344
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (360, 270) mm
(**) RADEON(0): DPI set to (126, 150)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
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
	compiled for 1.5.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
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
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1792,8191)
(II) RADEON(0): Reserved area from (0,1600) to (1792,1602)
(II) RADEON(0): Largest offscreen area available: 1792 x 6589
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1792x1344 - 2448 1394 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 204800000
best_freq: 204800000
best_feedback_div: 1024
best_ref_div: 27
best_post_div: 5
(II) RADEON(0): crtc(0) Clock: mode 204800, PLL 204800
(II) RADEON(0): crtc(0) PLL  : refdiv 27, fbdiv 0x400(1024), pdiv 5
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
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
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00af4000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00af9000
(II) RADEON(0): Largest offscreen area available: 1792 x 6583
(II) RADEON(0): Textured video requires CP on R5xx/IGP
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
(II) RADEON(0): Setting screen physical size to 360 x 270
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
AUDIT: Thu Sep 25 17:48:53 2008: 7451 X: client 4 rejected from local host ( uid=0 gid=0 pid=7859 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7914 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7915 )
AUDIT: Thu Sep 25 17:48:59 2008: 7451 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7916 )
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x1024 - 1688 1066 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 108000000
best_freq: 108000000
best_feedback_div: 48
best_ref_div: 2
best_post_div: 6
(II) RADEON(0): crtc(0) Clock: mode 108000, PLL 108000
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x30(48), pdiv 6
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(II) Open ACPI successful (/var/run/acpid.socket)
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success

```

---

### Post by sdowney717 on 2008-09-26
found this to get rid of abi version error
[http://forum.tuxx-home.at/viewtopic.php?f=10&t=78](http://forum.tuxx-home.at/viewtopic.php?f=10&t=78)

so I added to xorg.conf and still get errorr on glxinfo

```

scott@scott-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault (core dumped)
scott@scott-desktop:~$ gedit


```

how about this line in xorg log?

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

---

### Post by sdowney717 on 2008-09-26
got rid of several nvidia packages and now get more info 

```

scott@scott-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x22 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x83 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

17 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x84  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x85  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x86  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8e  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x90  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x91  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x92  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x93  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x93  0 dc  0 32  0 r  y  . 10 10 10  2  0 24  0  0  0  0  0  0 0 Slow

Segmentation fault (core dumped)
scott@scott-desktop:~$ 


```

now here is compiz

scott@scott-desktop:~$ compiz --replace
compiz (core) - Fatal: Root visual is not a double buffered GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Segmentation fault (core dumped)
scott@scott-desktop:~$ 



and the new xorg.o.log with no errors (EE)

```


(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux scott-desktop 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686
Build Date: 24 September 2008  06:28:32PM
xorg-server 2:1.5.1-1ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 26 13:50:26 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) Option "AIGLX" "true"
(**) Option "IgnoreABI" "True"
(**) Ignoring ABI Version
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
(**) Extension "Composite" is enabled
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

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] rev 0, Mem @ 0xe0000000/0, 0xf0400000/0, I/O @ 0x00002000/0, BIOS @ 0x????????/131072
(--) PCI: (0@1:0:1) ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary) rev 0, Mem @ 0xf0410000/0
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
	compiled for 1.5.1, module version = 1.0.0
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
	compiled for 1.5.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(**) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.9.0
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
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
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
(II) RADEON(0): MMIO registers at 0x00000000f0400000: size 64KB
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
	compiled for 1.5.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1300/X1550" (ChipID = 0x7142)
(WW) RADEON(0): R500 support is under development. Please report any issues to xorg-driver-ati@lists.x.org
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x030b
	IOBaseAddress: 0x2000
	Filename: SR20030.002 
	BIOS Bootup Message: 

PCP RV515Pro Rialto 256mb Infineon DDR2 BIOS 600e/400m Channel AB           


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 600000
(II) RADEON(0): Default Memory Clock: 405000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 405.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=13 min=64800 max=110000; xclk=40000
(II) RADEON(0): Skipping TV-Out
(II) RADEON(0): Skipping Component Video
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x7e40, DACType-1, TMDSType-0, ConnectorType-1, hpd_mask-0x0
(II) RADEON(0): Port9: DDCType-0x7e50, DACType-2, TMDSType-3, ConnectorType-2, hpd_mask-0x100
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): TMDS PLL from BIOS: 16500 a0115
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- LVTMA
 DDC Type  -- 0x7e50
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using fuzzy aspect match for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1792x1344
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (360, 270) mm
(**) RADEON(0): DPI set to (126, 150)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
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
	compiled for 1.5.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
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
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Using 32 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 29 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1792,8191)
(II) RADEON(0): Reserved area from (0,1600) to (1792,1602)
(II) RADEON(0): Largest offscreen area available: 1792 x 6589
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x2e0c000
(II) RADEON(0): Will use depth buffer at offset 0x38fc000
(II) RADEON(0): Will use 192512 kb for textures at offset 0x43ec000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 1x
(II) RADEON(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x2560; Card 0x1002/0x7142]
(II) RADEON(0): [agp] 32768 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf4000000
(II) RADEON(0): [agp] Ring mapped at 0xb78de000
(II) RADEON(0): [agp] ring read ptr handle = 0xf4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb78dd000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xa75f5000
(II) RADEON(0): [agp] GART texture map handle = 0xf4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xa5975000
(II) RADEON(0): [drm] register handle = 0xf0400000
(II) RADEON(0): [dri] Visual configs initialized
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1792x1344 - 2448 1394 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 204800000
best_freq: 204800000
best_feedback_div: 1024
best_ref_div: 27
best_post_div: 5
(II) RADEON(0): crtc(0) Clock: mode 204800, PLL 204800
(II) RADEON(0): crtc(0) PLL  : refdiv 27, fbdiv 0x400(1024), pdiv 5
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 18
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0xf5fff400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf5fff400
(II) RADEON(0): Direct rendering enabled
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
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00af4000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00af9000
(II) RADEON(0): Largest offscreen area available: 1792 x 6583
(II) RADEON(0): Set up textured video
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 360 x 270
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 enable success
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
AUDIT: Fri Sep 26 13:50:36 2008: 6942 X: client 4 rejected from local host ( uid=0 gid=0 pid=7355 )
AUDIT: Fri Sep 26 13:50:44 2008: 6942 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7419 )
AUDIT: Fri Sep 26 13:50:44 2008: 6942 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7420 )
AUDIT: Fri Sep 26 13:50:44 2008: 6942 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7421 )
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x1024 - 1688 1066 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf5fff400
freq: 108000000
best_freq: 108000000
best_feedback_div: 48
best_ref_div: 2
best_post_div: 6
(II) RADEON(0): crtc(0) Clock: mode 108000, PLL 108000
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x30(48), pdiv 6
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: STC  Model: 1871  Serial#: 16843009
(II) RADEON(0): Year: 2001  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.81
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!(II) RADEON(0): redX: 0.639 redY: 0.322   greenX: 0.274 greenY: 0.597
(II) RADEON(0): blueX: 0.141 blueY: 0.062   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 96 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: KDS XF-9e
(II) RADEON(0): Serial No: 000001
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004e83711801010101
(II) RADEON(0): 	000b01030c241bb5e8a734a352469824
(II) RADEON(0): 	0f484ca543008199615945593159a94f
(II) RADEON(0): 	010101010101863d00c05100304040a0
(II) RADEON(0): 	1300680e1100001e000000fd0032a01e
(II) RADEON(0): 	6015000a202020202020000000fc004b
(II) RADEON(0): 	44532058462d3965200a2020000000ff
(II) RADEON(0): 	003030303030310a2020202020200097
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "STC", prod id 6257
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
```

---

### Post by sdowney717 on 2008-09-26
I got direct rendering working now following this thread

[http://ubuntuforums.org/showthread.php?t=916805&highlight=Fatal%3A+Root+visual+double+buffered+GL&page=3](http://ubuntuforums.org/showthread.php?t=916805&highlight=Fatal%3A+Root+visual+double+buffered+GL&page=3)

but still dont have compiz working yet.

```

gscott@scott-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x83 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x84  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x85  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x86  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8e  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x90  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x91  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x92  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x93  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

scott@scott-desktop:~$ glxgears
7874 frames in 5.0 seconds = 1574.621 FPS
7886 frames in 5.0 seconds = 1577.119 FPS
7878 frames in 5.0 seconds = 1575.558 FPS
7850 frames in 5.0 seconds = 1569.240 FPS
^C
scott@scott-desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
scott@scott-desktop:~$ 


```

---

### Post by sdowney717 on 2008-09-26
ok, somehow compiz is working
I was getting an a final error
"GLX_EXT_texture_from_pixmap is missing"

a little googling told me to run a preload etc...
which I did and it errored

I then clicked fusion-icon selected emerald theme
and then I selected compiz window manager 
and it is working!


```

scott@scott-desktop:~$ glxgears
7874 frames in 5.0 seconds = 1574.621 FPS
7886 frames in 5.0 seconds = 1577.119 FPS
7878 frames in 5.0 seconds = 1575.558 FPS
7850 frames in 5.0 seconds = 1569.240 FPS
^C
scott@scott-desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

scott@scott-desktop:~$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/compiz.real --ignore-desktop-hints --indirect-rendering --replace ccp &
[1] 8080
scott@scott-desktop:~$ ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

[1]+  Exit 1                  LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/compiz.real --ignore-desktop-hints --indirect-rendering --replace ccp


scott@scott-desktop:~$ emerald --replace

(emerald:8089): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Reloading...
Reloading...
Terminated
scott@scott-desktop:~$ 



```

here is my working xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#EndSection

#Section "Device"
#        Identifier      "Configured Video Device"
#        Driver          "ati"
#        BusID           "PCI:1:0:0"
#EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "off"
        Option          "AGPMode"       "8"
        Option          "AGPFastWrite"  "1"
        Option		"EnablePageFlip"
        Option 		"ColorTiling"
	Option		"AGPMode"	"8"
	Option		"AGPFastWrite"	"1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"        
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "ServerFlags"
   Option "IgnoreABI" "True"
EndSection

```

---

### Post by PGHammer on 2008-09-29
> **sdowney717 said:**
> ok, somehow compiz is working
I was getting an a final error
"GLX_EXT_texture_from_pixmap is missing"

a little googling told me to run a preload etc...
which I did and it errored

I then clicked fusion-icon selected emerald theme
and then I selected compiz window manager 
and it is working!


```

scott@scott-desktop:~$ glxgears
7874 frames in 5.0 seconds = 1574.621 FPS
7886 frames in 5.0 seconds = 1577.119 FPS
7878 frames in 5.0 seconds = 1575.558 FPS
7850 frames in 5.0 seconds = 1569.240 FPS
^C
scott@scott-desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

scott@scott-desktop:~$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/compiz.real --ignore-desktop-hints --indirect-rendering --replace ccp &
[1] 8080
scott@scott-desktop:~$ ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

[1]+  Exit 1                  LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/compiz.real --ignore-desktop-hints --indirect-rendering --replace ccp


scott@scott-desktop:~$ emerald --replace

(emerald:8089): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Reloading...
Reloading...
Terminated
scott@scott-desktop:~$ 



```

here is my working xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#EndSection

#Section "Device"
#        Identifier      "Configured Video Device"
#        Driver          "ati"
#        BusID           "PCI:1:0:0"
#EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "off"
        Option          "AGPMode"       "8"
        Option          "AGPFastWrite"  "1"
        Option		"EnablePageFlip"
        Option 		"ColorTiling"
	Option		"AGPMode"	"8"
	Option		"AGPFastWrite"	"1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"        
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "ServerFlags"
   Option "IgnoreABI" "True"
EndSection

```

For some reason (this is with the radeonhd driver), while DRI works, it's far slower than the radeon driver (which is the default, and is likely *why* it's still the default with the X1K series).  I swapped the "radeonhd" driver for the default "radeon" driver by editing the "Device" section in xorg.conf (normally, no driver is specified, which loads the "radeon" driver by default).  Compiz (which was working with the default setup) still works; it's just slower than maple syrup at Barrow, AK.  I'm soon going to swap the "radeon" driver back in after some more testing of the "radeonhd" driver.

---

