---
title: "Jaunty, Radeon HD 3200 ERRORS"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Petro on 2009-03-14
The drivers (32bit) i downloaded from ati fail to load. I followed this tutorial [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Finally](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Finally)

and here's my Xorg.0.log 
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux DarkMatterU 2.6.28-9-generic #31-Ubuntu SMP Wed Mar 11 15:43:58 UTC 2009 i686
Build Date: 07 March 2009  02:18:57AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.000848] (--) probed, [    0.000862] (**) from config file, [    0.000872] (==) default setting,
	[    0.000881] (++) from command line, [    0.000891] (!!) notice, [    0.000901] (II) informational,
	[    0.000911] (WW) warning, [    0.000920] (EE) error, [    0.000930] (NI) not implemented, [    0.000940] (??) unknown.
[    0.001051] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 14 22:38:55 2009
[    0.001135] (==) Using config file: "/etc/X11/xorg.conf"
[    0.001306] (==) ServerLayout "aticonfig Layout"
[    0.001343] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.001353] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.001616] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.001646] (==) Automatically adding devices
[    0.001654] (==) Automatically enabling devices
[    0.001787] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.001839] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.001848] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001857] (II) Cannot locate a core pointer device.
[    0.001864] (II) Cannot locate a core keyboard device.
[    0.001871] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.001885] (II) Loader magic: 0x3bc0
[    0.001893] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.001921] (II) Loader running on linux
[    0.001931] (++) using VT number 7

[    0.043535] (--) PCI:*(0@1:5:0) ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] rev 0, Mem @ 0xc0000000/268435456, 0xd2300000/65536, 0xd2200000/1048576, I/O @ 0x00005000/256
[    0.043838] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.043923] (II) System resource ranges:
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
[    0.044768] (II) "extmod" will be loaded by default.
[    0.044776] (II) "dbe" will be loaded by default.
[    0.044783] (II) "glx" will be loaded by default.
[    0.044790] (II) "record" will be loaded by default.
[    0.044796] (II) "dri" will be loaded by default.
[    0.044803] (II) "dri2" will be loaded by default.
[    0.044812] (II) LoadModule: "extmod"
[    0.045227] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.045427] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.045459] (II) Loading extension MIT-SCREEN-SAVER
[    0.045466] (II) Loading extension XFree86-VidModeExtension
[    0.045473] (II) Loading extension XFree86-DGA
[    0.045482] (II) Loading extension DPMS
[    0.045489] (II) Loading extension XVideo
[    0.045497] (II) Loading extension XVideo-MotionCompensation
[    0.045504] (II) Loading extension X-Resource
[    0.045512] (II) LoadModule: "dbe"
[    0.045746] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.045838] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.045869] (II) Loading extension DOUBLE-BUFFER
[    0.045876] (II) LoadModule: "glx"
[    0.046112] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
[    0.046296] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.046308] (II) UnloadModule: "glx"
[    0.046316] (EE) Failed to load module "glx" (loader failed, 7)
[    0.046328] (II) LoadModule: "record"
[    0.046603] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.046715] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.046746] (II) Loading extension RECORD
[    0.046754] (II) LoadModule: "dri"
[    0.047018] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.047210] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
[    0.047231] (II) Loading extension XFree86-DRI
[    0.047248] (II) LoadModule: "dri2"
[    0.047529] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.047640] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.047665] (II) Loading extension DRI2
[    0.047674] (II) LoadModule: "fglrx"
[    0.047845] (II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.053218] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.58.2
	Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.4.-1.906
[    0.053589] (II) UnloadModule: "fglrx"
[    0.053598] (II) Unloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.053610] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)
[    0.053623] (EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

and here's xorg.conf
```
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
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:5:0"
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

oh and the comp is laptop HP TouchSmart TX2-1050eo :) thanks for help.

---

### Post by steveth45 on 2009-03-15
I had a very similar error when I upgrade from 8.10 to 9.04 alpha6. Basically, the fglrx driver isn't loading because it is wrongly detecting xorg as version 7.1 instead of 7.4. 7.4 is actually installed, so I don't know why this is happening.

---

### Post by Petro on 2009-03-15
> **steveth45 said:**
> I had a very similar error when I upgrade from 8.10 to 9.04 alpha6. Basically, the fglrx driver isn't loading because it is wrongly detecting xorg as version 7.1 instead of 7.4. 7.4 is actually installed, so I don't know why this is happening.

im guessing you didn't find solution to this and went back to 8.10 ? Im happy that you at least know somewhat what is causing this problem :) hopefully fixes or help comes soon.

---

### Post by Jayen on 2009-04-01
Jockey didn't detect my card, envyng used the 8.600 packages in the repository, with which I couldn't load the kernel module, and with ati's catalyst packages, I'm having the same problem as you, where I get the version mismatch.

No restricted drivers for me, I guess.

I'm using the jaunty beta.

---

### Post by super.rad on 2009-04-01
Just got my new pc today with Radeon HD3200 GPU and after a fresh jaunty beta install I just activated the FGLRX driver in jockey, restarted and it's all working fine with desktop effects

---

### Post by markbuntu on 2009-04-02
The 3200 was just added to jockey with the last update.

---

### Post by one51 on 2009-04-21
I am working with my first Linux PC, attempting to get away from W*ndows.  Bought an Asus M4A78 Pro with the 3200HD on board.

I was finally able to install the ATI driver 8.600 via Envy, BUT... although X loaded and things looked OK... I could barely drag windows around.  When I viewed video (DVD or AVI, using any program) it was very jerky, and maximizing the video window locked up the entire system.  This was the best I did after trying half a dozen different graphics drivers/setups.

The only driver that works for video (my main purpose) is the default from Jaunty (whatever that is), and then I get no 3D and no dual-monitor capability (which I need for my projector).

Should I try jockey as I am thinking here => does it do some different configuration than Envy, which might make things work?  Or do I have to wait for a better ATI driver (or buy an Nvidia card)?  Thanks in advance...

---

### Post by antiram on 2009-04-21
upstream ati radeon is here
[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

dual monitor:
if you use TV-out you must set 
Option "ATOMTvOut" "on"
in /etc/X11/xorg.conf Section "Device"

if you have no xorg.conf generate it with
sudo dpkg-reconfigure -phigh xserver-xorg

it is possible that the 2nd monitor must connected at startup of xserver.
modes can also be set with xrandr


my xorg.conf with 1* 1920x1200 and 1* TV-out clone mode is
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes   "1920x1200"
                Virtual 1920 1200
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "ATOMTvOut"             "on"
        Option          "TVStandard"            "pal"
        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
        Option          "EXAVSync"              "on"
EndSection

```

---

