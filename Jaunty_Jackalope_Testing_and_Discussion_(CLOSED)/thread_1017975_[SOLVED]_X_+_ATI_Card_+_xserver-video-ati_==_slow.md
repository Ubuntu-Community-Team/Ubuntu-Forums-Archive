---
title: "[SOLVED] X + ATI Card + xserver-video-ati == slow"
date: 2008-12-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-12-21
Hi guys, I'm experiencing a very slow 2D experience with my ati card (X1400) and the xserver-xorg-video-ati driver. Screen "painting" is very slow, and that is affecting everything, from rendering menus, to watching videos.

What is your experience with the new X and xserver-xorg-video-ati?

---

### Post by Progressive on 2008-12-21
I know that EXA wasn't set to on automatically in some ubuntu builds, so you can try setting Option "AccelMethod" "EXA" in xorg.conf.

If that isn't your problem it could be DRI2. As currently implemented, DRI2 in ATI causes a significant performance hit. You can turn it off in xorg.conf if you need to, but you will obviously lose the capability to run 3D applications with compositing on.

Of course if you don't even have compositing on, then I don't know what your problem is. You can try grabbing the latest code from git or turning on different things.

Cheers!

---

### Post by danf_1979 on 2008-12-21
Well, I finally went to #radeonhd on freenode, and had this short conversation:

```

<x1250> hi guys, I'm having a lot of performance issues with the ati opensource driver and my x1400. My problem is with 2D performance, its really bad, and can make Xorg use 100% CPU, make flash videos unviewable (1 frame per second), and window painting very slow (menus, etc)...
<x1250> here is my xorg log: http://paste.ubuntu.com/90381/
<x1250> xorg.conf: http://paste.ubuntu.com/90383/
<airlied> x1250: you need direct rendering, for some reason you don't yhave it
<x1250> xserver-xorg-video-ati is: 6.9.0+git20081003.f9826a56-0ubuntu6
<airlied> (EE) module ABI major version (1) doesn't match the server's version (2)
<airlied> the X server seems to be inconsistent
<airlied> you installed fglrx?
<airlied> you probably need to reinstall some packages
<x1250> uhm, yes, it is installed
<airlied> so its a local config issue, fglrx has trashed the X.org setup
<x1250> Ok, I'll get rid of the fglrx packages and restart x
<x1250> airlied, do I have to reinstall de opensource ati driver?
<airlied> x1250: you may have to reinstall the X server and mesa package
<airlied> not the ati one

```

So I removed all the fglrx packages:

```

$ sudo aptitude purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx

```

Reinstalled the mesa packages:

```

$ sudo aptitude reinstall libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils

```

And reinstall xorg packages:

```

$ sudo aptitude reinstall xorg xserver-xorg xserver-xorg-core

```

Then, I restarted X, and everything was ok again.

I'm using this xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by RAOF on 2008-12-22
> **danf_1979 said:**
> ...
I'm using this xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Note: you no longer need to explicitly enable EXA in Jaunty; it's used by default now.

---

### Post by RaZoR1394 on 2008-12-25
> **danf_1979 said:**
> Well, I finally went to #radeonhd on freenode, and had this short conversation:

```

<x1250> hi guys, I'm having a lot of performance issues with the ati opensource driver and my x1400. My problem is with 2D performance, its really bad, and can make Xorg use 100% CPU, make flash videos unviewable (1 frame per second), and window painting very slow (menus, etc)...
<x1250> here is my xorg log: http://paste.ubuntu.com/90381/
<x1250> xorg.conf: http://paste.ubuntu.com/90383/
<airlied> x1250: you need direct rendering, for some reason you don't yhave it
<x1250> xserver-xorg-video-ati is: 6.9.0+git20081003.f9826a56-0ubuntu6
<airlied> (EE) module ABI major version (1) doesn't match the server's version (2)
<airlied> the X server seems to be inconsistent
<airlied> you installed fglrx?
<airlied> you probably need to reinstall some packages
<x1250> uhm, yes, it is installed
<airlied> so its a local config issue, fglrx has trashed the X.org setup
<x1250> Ok, I'll get rid of the fglrx packages and restart x
<x1250> airlied, do I have to reinstall de opensource ati driver?
<airlied> x1250: you may have to reinstall the X server and mesa package
<airlied> not the ati one

```

So I removed all the fglrx packages:

```

$ sudo aptitude purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx

```

Reinstalled the mesa packages:

```

$ sudo aptitude reinstall libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils

```

And reinstall xorg packages:

```

$ sudo aptitude reinstall xorg xserver-xorg xserver-xorg-core

```

Then, I restarted X, and everything was ok again.

I'm using this xorg.conf:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

I've done exactly what you've done and also removed the EXA option and disabled DRI. It does not work for me unfortunately. I'm using a 3200HD gpu. Resolution of both monitors are fine but It's very slow in rendering. I pulled a git from here:

```

deb http://ppa.launchpad.net/xorg-edgers/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ubuntu jaunty main

```

My current xorg.conf

```

Section "Monitor"
	Identifier      "Configured Monitor"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Monitor         "Configured Monitor"
	Device          "Configured Video Device"
	SubSection "Display"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Device"
	Identifier      "Configured Video Device"
	Driver		"radeonhd"
	Option "DRI" 	"off"
EndSection

```

Also whenever there is something in xorg.conf that is inappropriate I get stuck at the ubuntu logo and the screen gets somewhat corrupt with a green dotted line. The best way to get out of that is to do MagicSYSRQ. CTR-ALT-DEL works only sometimes.

---

### Post by danf_1979 on 2008-12-26
Hi Razor, maybe you could post your /var/log/Xorg.0.log?

---

### Post by RaZoR1394 on 2008-12-26
Hi.

I removed Ubuntu Jaunty in favor of Sabayon 4.0 final as I didn't know where to go. But as that turned out to be more lika catastrophe as it was locking up all the time, I'm going to do a clean install of Jaunty alpha 2. I hope this issue isn't present then.

I didn't notice any severe errors in the Xorg log before I moved over to Sabayon. There was an (EE) about wacom_drv.so but I removed that one.

---

### Post by RaZoR1394 on 2008-12-27
This is my Xorg.0.log from fresh alpha 2 plus current updates...

Still pretty slow but a little bit better. I can't use fglrx on this machine because it makes it behave very bad so only options are radeon and radeonhd.

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.3
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux scorpia 2.6.28-3-generic #4-Ubuntu SMP Fri Dec 12 22:48:15 UTC 2008 i686
Build Date: 17 December 2008  03:10:17AM
xorg-server 2:1.5.99.3-0ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 27 06:42:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
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
(II) Loader magic: 0x1ac0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xc0000000/0, 0xd2400000/0, 0xd2300000/0, I/O @ 0x00006000/0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
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
	compiled for 1.5.99.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 6.9.0
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
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000d2400000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon HD 3200 Graphics" (ChipID = 0x9612)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000c0000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x103c SubsystemID: 0x30f1
	IOBaseAddress: 0x6000
	Filename: BR29066S.bin
	BIOS Bootup Message: 

HP_Soyuz20 RS780M DDR2 200e/500m                                            


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x13ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x13ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 500000
(II) RADEON(0): Default Memory Clock: 400000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 14320
(II) RADEON(0): Direct rendering not officially supported on RN50/RS600/R600
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=327680K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
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
(II) RADEON(0): ref_freq: 1432, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 500.000000, mclk: 400.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=12 min=64800 max=120000; xclk=40000
object id 0005 01
src object id 2115 21
record type 1
record type 4
object id 000a 01
src object id 2115 21
record type 4
object id 000e 01
src object id 211f 31
record type 1
record type 4
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output None has no monitor section
(II) RADEON(0): Output LVDS has no monitor section
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71110
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- SCART
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x7e50
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
finished output detect: 0
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
finished output detect: 1
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output None connected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Using sloppy heuristic for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1680x1050
(II) RADEON(0): Output None using initial mode 1360x768
(II) RADEON(0): Output LVDS using initial mode 1280x800
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (470, 300) mm
(**) RADEON(0): DPI set to (90, 135)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.
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
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Output 68 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x14000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00000000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1728,8191)
(II) RADEON(0): Reserved area from (0,1600) to (1728,1602)
(II) RADEON(0): Largest offscreen area available: 1728 x 6589
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00000000 0x00d300c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00a90000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00a95000
(II) RADEON(0): Largest offscreen area available: 1728 x 6583
Output 68 disable success
Output 68 disable success
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Lock CRTC 1 success
Output 68 disable success
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1280x800 - 1440 823 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00000000 0x00000000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 71110000
best_freq: 71102778
best_feedback_div: 715
best_ref_div: 12
best_post_div: 12
(II) RADEON(0): crtc(0) Clock: mode 71110, PLL 71100
(II) RADEON(0): crtc(0) PLL  : refdiv 12, fbdiv 0x2CB(715), pdiv 12
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DIG2 setup success
Output DIG2 transmitter setup success
Enable CRTC memreq 1 success
Enable CRTC 1 success
Unblank CRTC 1 success
Unlock CRTC 1 success
Output 68 enable success
Output DIG2 dpms success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Lock CRTC 0 success
Output DIG2 dpms success
Output 68 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Mode 1680x1050 - 2240 1089 6
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00000000 0x00000000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 146250000
best_freq: 146243000
best_feedback_div: 817
best_ref_div: 10
best_post_div: 8
(II) RADEON(0): crtc(1) Clock: mode 146250, PLL 146240
(II) RADEON(0): crtc(1) PLL  : refdiv 10, fbdiv 0x331(817), pdiv 8
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 1 setup success
Set CRTC 1 Source success
Output DAC1 setup success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Unlock CRTC 0 success
Output DIG2 dpms success
Output 68 enable success
Enable CRTC memreq 1 success
Enable CRTC 1 success
Unblank CRTC 1 success
Output 68 disable success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 342 x 213
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 2.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) AT Translated Set 2 keyboard: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device G15 Keyboard G15 Keyboard
(**) G15 Keyboard G15 Keyboard: always reports core events
(**) G15 Keyboard G15 Keyboard: Device: "/dev/input/event11"
(II) G15 Keyboard G15 Keyboard: Found keys
(II) G15 Keyboard G15 Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "G15 Keyboard G15 Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) G15 Keyboard G15 Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) G15 Keyboard G15 Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) G15 Keyboard G15 Keyboard: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) G15 Keyboard G15 Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Gaming Keyboard
(**) Gaming Keyboard: always reports core events
(**) Gaming Keyboard: Device: "/dev/input/event9"
(II) Gaming Keyboard: Found keys
(II) Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Gaming Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Gaming Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) Gaming Keyboard: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Gaming Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Gaming Keyboard
(**) Gaming Keyboard: always reports core events
(**) Gaming Keyboard: Device: "/dev/input/event10"
(II) Gaming Keyboard: Found keys
(II) Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Gaming Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Gaming Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) Gaming Keyboard: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Gaming Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) Video Bus: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Razer Razer Lachesis
(**) Razer Razer Lachesis: always reports core events
(**) Razer Razer Lachesis: Device: "/dev/input/event8"
(II) Razer Razer Lachesis: Found keys
(II) Razer Razer Lachesis: Configuring as keyboard
(II) XINPUT: Adding extended input device "Razer Razer Lachesis" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Razer Razer Lachesis: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Razer Razer Lachesis: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) Razer Razer Lachesis: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Razer Razer Lachesis: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
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
(II) config/hal: Adding input device Razer Razer Lachesis
(**) Razer Razer Lachesis: always reports core events
(**) Razer Razer Lachesis: Device: "/dev/input/event7"
(II) Razer Razer Lachesis: Found 8 mouse buttons
(II) Razer Razer Lachesis: Found x and y relative axes
(II) Razer Razer Lachesis: Configuring as mouse
(**) Razer Razer Lachesis: YAxisMapping: buttons 4 and 5
(**) Razer Razer Lachesis: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Razer Razer Lachesis" (type: MOUSE)
(**) Razer Razer Lachesis: (accel) keeping acceleration scheme 1
(**) Razer Razer Lachesis: (accel) filter chain progression: 2.00
(**) Razer Razer Lachesis: (accel) filter stage 0: 20.00 ms
(**) Razer Razer Lachesis: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event14"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device Wacom ISDv4 93
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.1-6 $
(**) Wacom ISDv4 93: always reports core events
(**) Wacom ISDv4 93 device is /dev/input/event13
(**) Wacom ISDv4 93 is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event13"
Wacom ISDv4 93 Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom USB TabletPC tablet speed=9600 (38400) maxX=26212 maxY=16420 maxZ=255 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom ISDv4 93" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356
AUDIT: Sat Dec 27 06:42:57 2008: 5476: client 4 rejected from local host ( uid=0 gid=0 pid=5637 )
AUDIT: Sat Dec 27 06:43:18 2008: 5476: client 4 rejected from local host ( uid=1000 gid=1000 pid=5735 )
AUDIT: Sat Dec 27 06:43:18 2008: 5476: client 4 rejected from local host ( uid=1000 gid=1000 pid=5736 )
AUDIT: Sat Dec 27 06:43:18 2008: 5476: client 4 rejected from local host ( uid=1000 gid=1000 pid=5737 )
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 254  Serial#: 1146106418
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
(II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HSAP100700
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004c2d540232325044
(II) RADEON(0): 	011101030e2f1e782ad515a455499a27
(II) RADEON(0): 	145054bfef80b30081808140714f0101
(II) RADEON(0): 	01010101010121399030621a274068b0
(II) RADEON(0): 	3600da281100001c000000fd00384b1e
(II) RADEON(0): 	5111000a202020202020000000fc0053
(II) RADEON(0): 	796e634d61737465720a2020000000ff
(II) RADEON(0): 	00485341503130303730300a202000ec
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SAM", prod id 596
(II) RADEON(0):     EDID quirk: Detailed timing is not preferred, use largest mode at 60Hz
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
in RADEONProbeOutputModes
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): EDID vendor "AUO", prod id 14356
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 3814  Serial#: 0
(II) RADEON(0): Year: 2007  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  261 x 163 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B121EW03 V8
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af143800000000
(II) RADEON(0): 	01110103801a10780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	360005a3100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231323145573033205638200a0009
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 14356

```

---

### Post by RaZoR1394 on 2008-12-28
Any news?

My current status is:

[http://pastebin.com/d2cdbb9bd](http://pastebin.com/d2cdbb9bd)

[http://pastebin.com/d65bd0c6c](http://pastebin.com/d65bd0c6c)

I've tried enabling dri, shadowfb and some other things without any success.

---

### Post by matrixblue on 2009-03-06
Your fix worked for me. Thanks!

---

### Post by arunthopil on 2009-03-19
hi the most easiest way is to install a smal package called envyng from synaptec manager........... it will get installed under applications system tools,,,,,,,,, it will help you selecting the best driver

read 

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

its easy

---

### Post by zika on 2009-03-19
> **arunthopil said:**
> hi the most easiest way is to install a smal package called envyng from synaptec manager........... it will get installed under applications system tools,,,,,,,,, it will help you selecting the best driver

read 

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

its easydoes it work in jaunty? I think not. but I've already answered You in numerous threads ...

---

### Post by arunthopil on 2009-03-19
you can try that ......otherwise if U r able to edit xorg.conf properly ..... U can make tht thing work..

---

### Post by amadeus266 on 2009-03-19
How are you able to mark the thread [SOLVED]??????? I can't figure it out!

---

### Post by smoosh on 2009-03-20
Fix worked for me!  I can now watch full length movies full screen (in Xine - other players are choppier) without a single tear!  From me or the movie... he he.  Thanks!

---

