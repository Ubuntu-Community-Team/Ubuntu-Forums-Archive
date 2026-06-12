---
title: "[SOLVED] unable to reconfigure X at terminal"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by johnapeterson on 2008-11-02
Hey gang,
I am one of the people having trouble getting to the GUI after upgrading from 8.04 to 8.10.  I get no splash screen or anything just the text log in.

I saw one forum thread that suggested reconfiguring X by typing:

Sudo X -configure

but when I do that I get the message that "/etc/X11/X is not executable"
Am I doing something wrong?

I did run the nvidia driver on 8.04, if I do get a fresh X will it automatically setup some default driver that would allow it to work in 8.10?

Thanks,
John

---

### Post by tuxxy on 2008-11-02
To reconfigure run this command then install the recommended drivers

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by johnapeterson on 2008-11-02
Ok,
When I try:
sudo dpkg -reconfigure xserver-xorg

I get the message:
dpkg: conflicting actions -e (--control) and -r (--remove)

Do I need to enter a different command before sudo dpkg -reconfigure xserver-xorg?

Thanks,
John

---

### Post by taurus on 2008-11-02
There shouldn't be a space between dpkg and -reconfigure.

```
sudo dpkg-reconfigure xserver-xorg
```

Otherwise, you can also run this command if you only want to reconfigure a driver for your graphic card.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by johnapeterson on 2008-11-02
Alright,
When I try sudo dpkg-reconfigure xserver-xorg

I get the following:
/usr/sbin/dpkg: xserver-xorg is broken or not fully installed

Do I need to remove the package first, and if so what would be the command?

Thanks for all your help.

John

---

### Post by cariboo on 2008-11-02
Try at the prompt:

```
sudo apt-get install -f
```

This will download any packages that didn't get installed properly.

Jim

---

### Post by johnapeterson on 2008-11-03
I tried:
sudo apt-get install -f

but got the following:
Reading package lists...Done
Building dependency tree
Reading State informaiton...Done
0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded

I assume that is did not work.

John

---

### Post by johnapeterson on 2008-11-03
Just wondering if maybe a the terminal I am not connected to the net, how could I check to see if I am connected to the net from the text log in I get?

Also, I keep having to switching between the harddrive (where I get text log in only) and the live CD (where I get gUI and am getting on to the forums).  Would there be a way to work on my hard drive problem without having to keep switching. (ie can I install xserver-xorg to the hard drive thru the Live CD)?

Would it also be possilbe to reinstall 8.10 onto the hard drive without is erasing my personal files that are already there?

Thanks,
John

---

### Post by cariboo on 2008-11-03
> Just wondering if maybe a the terminal I am not connected to the net, how could I check to see if I am connected to the net from the text log in I get?


If you are in recovery mode, you may not be connected, to make sure at the prompt type:

```
sudo dhclient eth0
```

> Also, I keep having to switching between the harddrive (where I get text log in only) and the live CD (where I get gUI and am getting on to the forums). Would there be a way to work on my hard drive problem without having to keep switching. (ie can I install xserver-xorg to the hard drive thru the Live CD)?


You could mount your hard drive while using the live CD and chroot the drive then make changes that will stick. To mount your hard drive while running the LiveCD in a terminal type:

```
sudo mount /dev/sdaX /mnt
``` 

Where /dev/sdaX is the partiton that you have Ubuntu installed on. then chroot the drive, in the same terminal type:

```
sudo chroot /mnt
```

Once in the chroot environment you could try:

```
dpkg-reconfigure -a
```

This will reconfigure partially installed packages.

Jim

---

### Post by johnapeterson on 2008-11-03
Hey Jim,
Thanks.  How would I know whether or not I am in the recovery mode?  Also, I know that my harddrive, when I am in the Live CD, is at the location /media/disk.  Would that be the same as the partition?  I am at work right now, but when I get home I will try your steps.

Thanks,
John

---

### Post by johnapeterson on 2008-11-03
Alright, 
Have tried the following:
Before I put in the live disk I ran:
dpkg-reconfigure -a
It ran me through a lot of menu like keyboard etc.  When I rebooted, I could still not get to the GUI, just the text login.

Set it up so I can work on the root on the hard drive thru the live cd.  If I run:
dpkg-reconfigure - a
I get (after an add user menu:

 Removing any system startup links for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease
   /etc/rc1.d/K20akiradrelease
   /etc/rc2.d/S20akiradrelease
   /etc/rc3.d/S20akiradrelease
   /etc/rc4.d/S20akiradrelease
   /etc/rc5.d/S20akiradrelease
   /etc/rc6.d/K20akiradrelease
OK
 Adding system startup for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc1.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc6.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc2.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc3.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc4.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc5.d/S20akiradrelease -> ../init.d/akiradrelease
invoke-rc.d: initscript atd, action "stop" failed.
invoke-rc.d: initscript atd, action "start" failed.

For:
apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# 

For:
dpkg-reconfigure xserver-xorg

/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed
root@ubuntu:/# 

If I try:
apt-get install xserver-xorg-core

I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xserver-xorg-core has no installation candidate


Any help would be greatly appreciated.
John

---

### Post by taurus on 2008-11-03
Try the xserver-xorg package instead of the xserver-xorg-core.

```
sudo apt-get update
sudo apt-get install xserver-xorg
```

---

### Post by johnapeterson on 2008-11-03
After I install xserver-xorg and then run sudo X -configure,
the file xorg.conf.new creates this:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
EndSection

Section "Module"
	Load  "xtrap"
	Load  "dbe"
	Load  "glx"
	Load  "extmod"
	Load  "dri"
	Load  "record"
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
	#DisplaySize	  320   240	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL E770s"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7300 GT"
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




When I test run this file the X.0.log comes up with this (sorry I do not know how to do the scroll box):


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux john 2.6.24-21-rt #1 SMP PREEMPT RT Wed Oct 22 01:36:03 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  3 19:28:48 2008
(++) Using config file: "/home/john/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/misc").
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/100dpi/".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/100dpi/").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/75dpi/".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/75dpi/").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/Type1".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/Type1").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/100dpi".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/100dpi").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/75dpi".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/75dpi").
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 7300 GT rev 162, Mem @ 0xe4000000/0, 0xd0000000/0, 0xe5000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "xtrap"

(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DEC-XTRAP
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
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
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce 7300 GT at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 7300 GT"
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xE4000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: VHT  Model: dddd  Serial#: 1
(II) NV(0): Year: 2003  Week: 4
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Signal levels configurable
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.85
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.333   greenX: 0.285 greenY: 0.595
(II) NV(0): blueX: 0.152 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NV(0): #1: hsize: 640  vsize 480  refresh: 70  vid: 18993
(II) NV(0): #2: hsize: 800  vsize 600  refresh: 70  vid: 19013
(II) NV(0): #3: hsize: 1024  vsize 768  refresh: 72  vid: 19553
(II) NV(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #5: hsize: 1280  vsize 1024  refresh: 70  vid: 35457
(II) NV(0): #6: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) NV(0): #7: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Serial No: 023500000001
(II) NV(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
(II) NV(0): Monitor name: PV1710
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff005914dddd01000000
(II) NV(0): 	040d010318221bb9ea9119a255499827
(II) NV(0): 	10484cbfef003140314a454a614c8180
(II) NV(0): 	818a818c8140ea240060410028303060
(II) NV(0): 	130036e61000001e000000ff00303233
(II) NV(0): 	3530303030303030310a000000fd0032
(II) NV(0): 	4b1e520e000a202020202020000000fc
(II) NV(0): 	0050563137313020202020202020007f
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: 300a  Serial#: 1112945457
(II) NV(0): Year: 2000  Week: 50
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.26
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.645 redY: 0.321   greenX: 0.285 greenY: 0.600
(II) NV(0): blueX: 0.142 blueY: 0.057   whiteX: 0.281 whiteY: 0.311
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Serial No: 2010V0CDBV31
(II) NV(0): Monitor name: DELL E770s
(II) NV(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac0a3031335642
(II) NV(0): 	320a01026820187eea1262a552499924
(II) NV(0): 	0e484fa54a0061593159818001010101
(II) NV(0): 	010101010101ea240060410028303060
(II) NV(0): 	130032e61000001e000000ff00323031
(II) NV(0): 	3056304344425633310a000000fc0044
(II) NV(0): 	454c4c2045373730730a2020000000fd
(II) NV(0): 	0032a01e460b000a20202020202000cf
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "VHT", prod id 56797
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) NV(0): Modeline "640x480"x70.0   28.56  640 664 728 816  480 481 484 500 -hsync +vsync (35.0 kHz)
(II) NV(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) NV(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) NV(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
(II) NV(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor0: Using hsync range of 30.00-70.00 kHz
(II) NV(0): Monitor0: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Monitor0: Using maximum pixel clock of 140.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Driver mode "1280x1024": 108.9 MHz, 63.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0): *Driver mode "1280x960": 102.1 MHz, 59.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Driver mode "1024x768": 78.4 MHz, 57.7 kHz, 72.0 Hz
(II) NV(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
(**) NV(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Driver mode "800x600": 45.5 MHz, 43.8 kHz, 70.0 Hz
(II) NV(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Driver mode "640x480": 28.6 MHz, 35.0 kHz, 70.0 Hz
(II) NV(0): Modeline "640x480"x70.0   28.56  640 664 728 816  480 481 484 500 -hsync +vsync (35.0 kHz)
(**) NV(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "640x480": 23.9 MHz, 29.8 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) NV(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) NV(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) NV(0): Display dimensions: (340, 270) mm
(**) NV(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
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
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI capable
(EE) AIGLX error: dlopen of /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
(EE) GLX: could not load software renderer
(II) GLX: no usable GL providers found for screen 0
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/input/mice"
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Mouse0: Buttons: 11
(**) Mouse0: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

Fatal server error:
could not open default font 'fixed'
(II) UnloadModule: "mouse"
(II) UnloadModule: "kbd"


What should I do next?

Thanks,
John

PS: I do not actuall know what driver need to work with my GeForce 7300.  I know that there are some issues with the current nvidia drivers.

---

### Post by taurus on 2008-11-03
Instead of running "sudo X -configure", why not try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by johnapeterson on 2008-11-03
Tried using
sudo dpkg-reconfigure xserver-xorg

the resulting xorg.conf file is:

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

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I am still not getting the desktop.  I have noticed thou that without a splash screen I get the text as things boot up.  It move by pretty quick, but two thing I do notice:

1) at the beginning the first line of text is something like:
     usb 1-1 device not accepting address 2 error -71

2) and near the end:
   Nvidia (177.80)        [FAIL]

Thanks for help.
John

---

### Post by taurus on 2008-11-03
Run that command again but this time, pick nv as your graphic card driver.

```
sudo dpkg-reconfigure xserver-xorg
```
Otherwise, use the -phigh option then.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by johnapeterson on 2008-11-03
I forgot to mention that when I run 
sudo dpkg-reconfigure xserver-xorg

I only get the options for choosing keyboards, and then it will go right back to the prompt.  It seems that I never get to a point where I can choose the nv driver.

John

---

### Post by johnapeterson on 2008-11-04
Here is what I did this morning, and where I am at right now:

when I only get text login, I do not seem to have a net connection so I type:

sudo dhclient eth0

I figured I needed to get rid of my current version of xserver-xorg completely so:

sudo apt-get remove --purge xserver-xorg
sudo apt-get clean
sudo apt-get update
sudo apt-get install xserver-xorg

So far everything seems to be going ok, but if I try:

sudo dpkg-reconfigure xserver-xorg

I get into a simple graphics menu where I can choose my keyboard options, but then it gets out of the graphics menu and tells me that it is overwritting a customized xorg.conf file and make a back up, and then I get the command prompt again.  So I never get beyond the keyboard part of the menu.

So then I tried:

sudo X -configure

I copied the resulting xorg.conf.new to xorg.conf and my current xorg.conf looks like this (I still have my problem of not getting the desktop):

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
EndSection

Section "Module"
	Load  "xtrap"
	Load  "dbe"
	Load  "glx"
	Load  "extmod"
	Load  "dri"
	Load  "record"
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
	#DisplaySize	  320   240	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL E770s"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7300 GT"
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




**My xorg.0.log file has the following output:**


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux john 2.6.24-21-rt #1 SMP PREEMPT RT Wed Oct 22 01:36:03 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  4 07:57:22 2008
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 7300 GT rev 162, Mem @ 0xe4000000/0, 0xd0000000/0, 0xe5000000/0, BIOS @ 0x????????/131072
List of video drivers:
	neomagic
	voodoo
	mga
	radeon
	openchrome
	r128
	i128
	chips
	apm
	nv
	siliconmotion
	i740
	v4l
	trident
	s3
	s3virge
	ztv
	savage
	sisusb
	i810
	tdfx
	vmware
	tseng
	cirrus
	ati
	intel
	mach64
	ark
	rendition
	sis
	geode
	fbdev
	vesa
(II) LoadModule: "neomagic"

(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "voodoo"

(II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mga"

(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "openchrome"

(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.1, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i128"

(II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "chips"

(II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "apm"

(II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "siliconmotion"

(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i740"

(II) Loading /usr/lib/xorg/modules/drivers//i740_drv.so
(II) Module i740: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "v4l"

(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "trident"

(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3"

(II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3virge"

(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ztv"

(II) Loading /usr/lib/xorg/modules/drivers//ztv_drv.so
(II) Module ztv: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 0.0.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "savage"

(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "sisusb"

(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i810"

(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "tdfx"

(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vmware"

(II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 10.16.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "tseng"

(II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "cirrus"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Failed to load module "intel" (already loaded, -1078719900)
(II) LoadModule: "mach64"

(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ark"

(II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.7.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "rendition"

(II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "sis"

(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "geode"

(II) Loading /usr/lib/xorg/modules/drivers//geode_drv.so
(II) Module geode: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "fbdev"

(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for neomagic
(WW) Falling back to old probe method for voodoo
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for apm
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for i740
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(WW) Falling back to old probe method for trident
(WW) Falling back to old probe method for s3
(WW) Falling back to old probe method for s3virge
(WW) Falling back to old probe method for z4l
(II) z4l driver for Video4Linux
(WW) Falling back to old probe method for sisusb
(WW) Falling back to old probe method for tseng
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(WW) Falling back to old probe method for ark
(WW) Falling back to old probe method for sis
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(++) Using config file: "/home/john/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/misc").
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/100dpi/".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/100dpi/").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/75dpi/".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/75dpi/").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/Type1".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/Type1").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/100dpi".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/100dpi").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/75dpi".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/X11/75dpi").
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) ModulePath set to "/usr/lib/xorg/modules"
(--) NV: Found NVIDIA GeForce 7300 GT at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(II) NV(0): VESA BIOS detected
(II) NV(0): VESA VBE Version 3.0
(II) NV(0): VESA VBE Total Mem: 262144 kB
(II) NV(0): VESA VBE OEM: NVIDIA
(II) NV(0): VESA VBE OEM Software Rev: 5.115
(II) NV(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) NV(0): VESA VBE OEM Product: G73 Board - p508h0  
(II) NV(0): VESA VBE OEM Product Rev: Chip Rev   
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): VESA VBE DDC supported
(II) NV(0): VESA VBE DDC Level 2
(II) NV(0): VESA VBE DDC transfer in appr. 1 sec.
(II) NV(0): VESA VBE DDC read successfully


Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is /home/john/xorg.conf.new

To test the server, run 'X -config /home/john/xorg.conf.new'


**Is there another log file that I can show that might be of help with this problem (like syslog)?  It goes thru the bootup process when I turn the computer on, but I do not know exactly what log file contains that data.**

Thanks again,
John

---

### Post by johnapeterson on 2008-11-04
Maybe I should also mentio that I run two monitors on my GeForce 7300 video card.  Both are mirrored in the text only log in and on the Live CD.  Could this be problem with my x starting up?  I would like to get to the desktop first and then worry about setting up my big screen.

Once again would there be any logs that I can post that might be helpful for someone to see what is going on?

Thanks,
John

---

### Post by taurus on 2008-11-04
Unplug the second monitor.  Then, run this again

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And please do not run the "sudo X -configure".

Otherwise, you can look in /var/log/Xorg.0.log.

```
cat /var/log/Xorg.0.log | more
```
Hit the space bar for the next 24 lines.

---

### Post by johnapeterson on 2008-11-04
Thanks,
I will try that when I get home this afternoon and report back.

John

---

### Post by nmltom on 2008-11-04
Sorry for breaking in, but I have upgraded from 6.06 to 8.04 to 8.10 and my keyboard and mouse are not working in GDM.  I tried to follow your instructions, quoted below, but when I ran:
sudo apt-get install xserver-xorg

I get the message that xserver-xorg is already the newest version.

Do you have any suggestions for steps that might get my keyboard and mouse back in GDM?  I saw some recommendations to edit xorg.conf to put the input device parameters for the mouse and the keyboard back in.  I did that and got the keyboard to respond, but not the mouse.  I would be grateful for some additional steps to follow.

Thank you.


> **taurus said:**
> Try the xserver-xorg package instead of the xserver-xorg-core.

```
sudo apt-get update
sudo apt-get install xserver-xorg
```

---

### Post by taurus on 2008-11-04
> **nmltom said:**
> Sorry for breaking in, but I have upgraded from 6.06 to 8.04 to 8.10 and my keyboard and mouse are not working in GDM.  I tried to follow your instructions, quoted below, but when I ran:
sudo apt-get install xserver-xorg

I get the message that xserver-xorg is already the newest version.

Do you have any suggestions for steps that might get my keyboard and mouse back in GDM?  I saw some recommendations to edit xorg.conf to put the input device parameters for the mouse and the keyboard back in.  I did that and got the keyboard to respond, but not the mouse.  I would be grateful for some additional steps to follow.

Thank you.

Try

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by nmltom on 2008-11-04
Thank you.  I tried this:
sudo dpkg-reconfigure xserver-xorg
Here is the gist of what I got:
Gtk warning   cannot open display
debconf   unable to initialize front end: Gnome
          (DISPLAY problem?)
          falling back to front end: Dialog
Package "xserver-org" is not installed and no info is available

That is the result of the first command.  After that I tried to: 
startx

And basically the error message came back that is was already running (which is true since the login screen was on tty 7.

I am in way over my head.  What now?

---

### Post by johnapeterson on 2008-11-04
Hey taurus,
what will I be looking for when I type in:

cat /var/log/Xlog.0.log | more

And why do I need to hit the space bar for the next 24 line?

Thanks,
John

---

### Post by johnapeterson on 2008-11-04
Ok,

After unplugging one of my monitors and running:
sudo dpkg-reconfigure xserver-xorg

(I should note that the simple graphics set up of running this only goes thru the keyboard and then bumps me back to the command prompt)

My xorg.conf looks like this:

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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I am not getting an desktop at all.  I looked to see if the computer generated a /var/log/xorg.0.log and it did not.

Are there any other logs that I can post that might be able to hhelp someone to tell me what I am going to need to do?

Thanks,
John

---

### Post by johnapeterson on 2008-11-05
Trying to work up a plan B if I cannot get this thing to work.

Would there be a way that I can get to me evolution address book on my harddrive thru the Live CD, and transfer it to an external harddrive?

Where on the harddrive would my bookmarks for Foxfire be located so I might be able to transfer them?

Can I get permission to transfer my files from my harddrive to the external harddrive thru the Live CD, and if so how?

This is just a plan B in case I cannot get this text login thing resolved.  I would really love to get that back going, so I do not have to do a complete restall and load up all the applications I like to us again.

Thank,
John

---

### Post by johnapeterson on 2008-11-05
I should also mention that I did have Ubuntu Studio 8.4, would it be advisiable to try to upgrade to ubuntu studio 8.10 instead of ubuntu 8.10?

If it would be better for me to upgrade to studio 8.10 instead, how would I do it, and would it wipe out my personal files on the harddrive?

Thanks,
John

---

### Post by zvacet on 2008-11-05
Read [this]("https://wiki.ubuntu.com/X/Config") and see if it is helpful to you.

---

### Post by johnapeterson on 2008-11-05
This morning I tried
sudo dpkg-reconfigure -a

Right before the blue screen pops up, I see a few lines of text.  The blue screen comes up pretty quick, but one of the lines does read:
"unable to load grub"

Is that a hint to anyone?

Thanks,
John

---

### Post by johnapeterson on 2008-11-05
As I mentioned before when I run:
sudo dpkg-reconfigure xserver-xorg
and
sudo dpkg-reconfigure -a

I never get to a screen where I can choose video drivers.  Reconfiguring xserver-xorg only goes thru the keyboard setup and then bumps me back to the command prompt.

And as I mentioned in a previous post, when typing dpkg-reconfigure -a, right before the blue screen comes up, there are about three lines of text.  The blue screen comes up pretty quick, but one of the text lines does read:
"unable to load grub"

I do not know if that has anything to do with my problem.

John

---

### Post by johnapeterson on 2008-11-05
Could my grub be messed up.  Would reinstall grub be worth it to try to fix the problem, if so how is the best way to do it?

Thansk,
John

---

### Post by johnapeterson on 2008-11-05
Could my grub be messed up.  Would reinstall grub be worth it to try to fix the problem, if so how is the best way to do it?

Thansk,
John

---

### Post by johnapeterson on 2008-11-05
I solved my problem by reinstalling ubuntu studio.  I now have a different problem I will list on a new thread ( after seeing if anyone else had problem).

Thanks for everyones help.

John

---

### Post by nmltom on 2008-11-06
Hello Zvacet:

I followed the link to the wiki and Input Device Configuration.  I tried the first command it suggests:
 $ xinput list

I got the message: "Unable to connect to the X Server"

Can you recommend further steps?  Thx.

---

