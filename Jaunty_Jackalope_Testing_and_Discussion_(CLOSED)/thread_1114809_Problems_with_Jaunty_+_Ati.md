---
title: "Problems with Jaunty + Ati"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fipoo on 2009-04-03
Hello!
I'm having some problems after installing fglrx drivers on my new Kubuntu Jaunty recently downloaded distro.

I have a laptop with an Ati HD 2400 video card. The first thing I done after installing the sistem (alternate install) was try to install the fglrx drivers, everything gone ok, i mean, with no errors. Then, I run:
```
aticonfig --initial
aticonfig --resolution-0,1280x800
```

After that, I rebooted my system and what I got was a totally black screen just after the graphical boot.
With that black screen, I was unable to do nothing, except rebooting by pressing the power button.
Then, I restarted the system in recovery mode and got the log files. Here they are:
[HTML]

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux KubuntuFipoo 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64
Build Date: 20 March 2009  02:02:41PM
xorg-server 2:1.6.0-0ubuntu4 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.058568] (--) probed, [    0.058583] (**) from config file, [    0.058592] (==) default setting,
	[    0.058601] (++) from command line, [    0.058610] (!!) notice, [    0.058618] (II) informational,
	[    0.058627] (WW) warning, [    0.058635] (EE) error, [    0.058644] (NI) not implemented, [    0.058653] (??) unknown.
[    0.058746] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  2 22:46:08 2009
[    0.072687] (==) Using config file: "/etc/X11/xorg.conf"
[    0.072837] (==) ServerLayout "aticonfig Layout"
[    0.072851] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.101158] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.101475] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.101502] (==) Automatically adding devices
[    0.101511] (==) Automatically enabling devices
[    0.139508] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.257255] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.257278] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.257287] (II) Cannot locate a core pointer device.
[    0.257294] (II) Cannot locate a core keyboard device.
[    0.257300] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.257319] (II) Loader magic: 0xb40
[    0.257326] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.257352] (II) Loader running on linux
[    0.257364] (++) using VT number 7

[    0.288548] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 2400 rev 0, Mem @ 0xd0000000/134217728, 0xd8000000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    0.288850] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.288907] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.289035] (II) "extmod" will be loaded by default.
[    0.289044] (II) "dbe" will be loaded by default.
[    0.289050] (II) "glx" will be loaded by default.
[    0.289057] (II) "record" will be loaded by default.
[    0.289063] (II) "dri" will be loaded by default.
[    0.289070] (II) "dri2" will be loaded by default.
[    0.289080] (II) LoadModule: "extmod"
[    0.320658] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.320964] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.321008] (II) Loading extension MIT-SCREEN-SAVER
[    0.321017] (II) Loading extension XFree86-VidModeExtension
[    0.321023] (II) Loading extension XFree86-DGA
[    0.321029] (II) Loading extension DPMS
[    0.321036] (II) Loading extension XVideo
[    0.321044] (II) Loading extension XVideo-MotionCompensation
[    0.321051] (II) Loading extension X-Resource
[    0.321061] (II) LoadModule: "dbe"
[    0.321374] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.321488] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.321551] (II) Loading extension DOUBLE-BUFFER
[    0.321560] (II) LoadModule: "glx"
[    0.321830] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.322065] (II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.322114] (II) Loading extension GLX
[    0.322125] (II) LoadModule: "record"
[    0.322417] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.322548] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.322586] (II) Loading extension RECORD
[    0.322595] (II) LoadModule: "dri"
[    0.322865] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.338377] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.338418] (II) Loading extension XFree86-DRI
[    0.338427] (II) Loading sub module "fglrxdrm"
[    0.338433] (II) LoadModule: "fglrxdrm"
[    0.338499] (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
[    0.358571] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
[    0.358627] (II) LoadModule: "dri2"
[    0.358930] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.367752] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.367795] (II) Loading extension DRI2
[    0.367807] (II) LoadModule: "fglrx"
[    0.367976] (II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.917744] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
	Module class: X.Org Video Driver
[    0.949020] (II) Primary Device is: PCI 01@00:00:0
[    0.949042] (WW) Falling back to old probe method for fglrx
[    0.949051] (II) ATI Proprietary Linux Driver Version Identifier:8.60.40
[    0.949059] (II) ATI Proprietary Linux Driver Release Identifier: 8.60.4                               
[    0.949065] (II) ATI Proprietary Linux Driver Build Date: Mar 14 2009 21:46:40
[    1.104402] (II) Loading PCS database from /etc/ati/amdpcsdb
[    1.104452] (WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
[    1.104461] (WW) Video driver ABI version of the X server is 5.0
[    1.104995] (--) Chipset Supported AMD Graphics Processor (0x94C9) found
[    1.105220] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    1.105536] (II) AMD Video driver is signed
[    1.114098] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    1.114269] (II) fglrx(0): pEnt->device->identifier=0xa71a80
[/HTML]
As you can see, the log doesn't displays any error... strange.

and here is my xorg.conf file:
[HTML]
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
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
[/HTML]

By the way, to get my system working again, i removed the xorg-driver-fglrx package and comented the two lines from my xorg.conf:
[HTML]
Driver      "fglrx"
BusID       "PCI:1:0:0"
[/HTML]

My question is: Why there is no error in the log file, and either I didn't got any errors in the fglrx-driver installation?
Is there anybody who knows how to solve it?
Thanks, FiPoO!

---

