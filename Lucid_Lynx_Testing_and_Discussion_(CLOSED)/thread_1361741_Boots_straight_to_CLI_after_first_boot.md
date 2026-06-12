---
title: "Boots straight to CLI after first boot"
date: 2009-12-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ST3ALTHPSYCH0 on 2009-12-22
I've installed twice and had the same problem both times. I can boot to a DE the first time I boot, but after a reboot it takes me straight to a CLI logon. The first time I installed the proprietary Nvidia driver, but the second time I didn't. The first time I tried updating, but that didn't help. I also used Envy to remove the driver, but that didn't change anything either. Finally, I tried installing KDE to see if it was a Gnome problem, but I was still dumped to CLI.

My machine specs are:
AMD Sempron 2200+
512 Mb RAM
Nvidia Geforce4 MX440

I'm using alpha trying to advocate for legacy hardware, but it's not looking good so far.... guess that's what happens when a Linux n00b uses an alpha release!

---

### Post by ranch hand on 2009-12-22
De?

---

### Post by phillw on 2009-12-22
> **ranch hand said:**
> De?

I'm guessing Desktop Environment, as opposed to CLI

Phill.

---

### Post by ranch hand on 2009-12-22
OK, I am always glad to be proven right.  I always did think I was simple.

---

### Post by phillw on 2009-12-22
This is from someone else (on 9.10) who was having problems getting their nvid to behave .. It may be of help to you.

> I'm getting the problems licked one by one.  Nvidia settings lack of persistence is the only one remaining. 			 		 	 	 Run the nvidia-settings as root from terminal  	```

	gksu nvidia-settings
``` 


Regards,

Phill.

---

### Post by ST3ALTHPSYCH0 on 2009-12-22
I'll give it a try, but I'm not sure that I can run that from a prompt.... what's the nvidia config command?

***EDIT****
found it:
```

sudo *nvidia*-xconfig -t

```I'll reboot into Lucid after I get done with this game of scorched earth (the original DOS version hehe)

EDIT#2

Well, I don't have the Nvidia driver installed, so nvidia-xconfig is out. I tried dpkg-reconfigure -phigh xserver-xorg, and I still get a CLI. I d/led the latest round of updates and I still can't get a GUI, and I can't boot to the -9 kernel. Sigh, I know it's an alpha, but the Lynx and I are off to a rough start.

---

### Post by ST3ALTHPSYCH0 on 2009-12-23
Well, evidently, there's a problem with the xorg.conf that worked fine with 8.04,9.04,&9.10, because when I renamed it and let the machine make a new one I went straight to the graphical login. I don't mind working with 800x600 for a little while. 

My problem now is that my mouse pointer just sits in the middle of the screen jiggling around. Any ideas? A GUI is a little cumbersome without a mouse

******EDIT****************
Evidently, there's no mouse configured according to the xorg.5.log:
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.7.3.901 (1.7.4 RC 1)
Release Date: 2009-12-11
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux lucidblair-desktop 2.6.32-9-generic #13-Ubuntu SMP Thu Dec 17 17:02:51 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-9-generic root=UUID=fc695765-d3dd-420d-9bee-99d0ad086304 ro quiet splash
Build Date: 19 December 2009  03:03:24AM
xorg-server 2:1.7.3.901-1ubuntu3 (buildd@) 
Current version of pixman: 0.16.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.000000] (--) probed, [    0.000033] (**) from config file, [    0.000051] (==) default setting,
    [    0.000067] (++) from command line, [    0.000084] (!!) notice, [    0.000101] (II) informational,
    [    0.000117] (WW) warning, [    0.000133] (EE) error, [    0.000149] (NI) not implemented, [    0.000166] (??) unknown.
[    0.007055] (==) Log file: "/var/log/Xorg.5.log", Time: Wed Dec 23 14:15:07 2009
[    0.007247] (==) Using config file: "/etc/X11/xorg.conf"
[    0.007928] (==) ServerLayout "Default Layout"
[    0.007961] (**) |-->Screen "Default Screen" (0)
[    0.007986] (**) |   |-->Monitor "Configured Monitor"
[    0.008620] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    0.008652] (**) |   |-->Device "device1"
[    0.008709] (==) Automatically adding devices
[    0.008730] (==) Automatically enabling devices
[    0.008890] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    0.009024] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    0.009047] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.009067] (II) Cannot locate a core pointer device.
[    0.009086] (II) Cannot locate a core keyboard device.
[    0.009103] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    0.009128] (II) Loader magic: 0x81eeea0
[    0.009142] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
[    0.009232] (--) using VT number 7

[    0.192858] (--) PCI:*(0:2:0:0) 10de:0171:0000:0000 nVidia Corporation NV17 [GeForce4 MX 440] rev 163, Mem @ 0xea000000/16777216, 0xd8000000/134217728, 0xe0000000/524288, BIOS @ 0x????????/131072
[    0.196337] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.196421] (II) "extmod" will be loaded by default.
[    0.196450] (II) "dbe" will be loaded by default.
[    0.196468] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    0.196487] (II) "record" will be loaded by default.
[    0.196505] (II) "dri" will be loaded by default.
[    0.196523] (II) "dri2" will be loaded by default.
[    0.196554] (II) LoadModule: "glx"
[    0.197103] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    0.197489] (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.197590] (==) AIGLX enabled
[    0.197620] (II) Loading extension GLX
[    0.197642] (II) LoadModule: "v4l"
[    0.198045] (II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
[    0.198200] (II) Module v4l: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 0.1.1
    ABI class: X.Org Video Driver, version 6.0
[    0.198306] (II) LoadModule: "extmod"
[    0.198504] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    0.198761] (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.198854] (II) Loading extension MIT-SCREEN-SAVER
[    0.198869] (II) Loading extension XFree86-VidModeExtension
[    0.198881] (II) Loading extension XFree86-DGA
[    0.198897] (II) Loading extension DPMS
[    0.198910] (II) Loading extension XVideo
[    0.198925] (II) Loading extension XVideo-MotionCompensation
[    0.198938] (II) Loading extension X-Resource
[    0.198952] (II) LoadModule: "dbe"
[    0.199118] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    0.199277] (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.199366] (II) Loading extension DOUBLE-BUFFER
[    0.199381] (II) LoadModule: "record"
[    0.199568] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    0.199744] (II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.199833] (II) Loading extension RECORD
[    0.199849] (II) LoadModule: "dri"
[    0.200023] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    0.208563] (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.208723] (II) Loading extension XFree86-DRI
[    0.208756] (II) LoadModule: "dri2"
[    0.209019] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    0.209217] (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
[    0.209301] (II) Loading extension DRI2
[    0.209320] (II) LoadModule: "vesa"
[    0.209966] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    0.210123] (II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.2, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
[    0.210207] (II) v4l driver for Video4Linux
[    0.210230] (II) VESA: driver for VESA chipsets: vesa
[    0.210348] (II) Primary Device is: PCI 02@00:00:0
[    0.210362] (WW) Falling back to old probe method for v4l
[    0.210512] (EE) Screen 0 deleted because of no matching config section.
[    0.210542] (II) UnloadModule: "vesa"
[    0.210557] (EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

```
I'm gonna keep playing, but some specific instructions on configuration would be peachy. I haven't ever had a mouse in Lucid come to think of it

---

### Post by phillw on 2009-12-23
Now, don't snigger, coz I'm no expert on this ... but ... comparing line for line your log file & mine... There is something which jumps out and bites me ....

> [    0.007247] (==) Using config file: "/etc/X11/xorg.conf"As in, I don't have that line. In fact, I don't even have a ```

/etc/X11/xorg.conf 
``` !!!!

So, I think our system architecture must be quite different (I'm using bog-standard intel graphics chip in my lap-top)

If you think it may be nvidia card related, the thread over for 9.10 is quite good --> [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

As your system seems to complain before it gets to mouse / touchpad detection area, maybe solving the graphics will sort your rodent out ?

Soz that I can't help you any further :-(

Phill.

---

### Post by ranch hand on 2009-12-23
A xorg.conf file should be generated if there is a need for one.

---

### Post by ST3ALTHPSYCH0 on 2009-12-23
It will auto generate an xorg.conf file every time, it just doesn't want to see the mouse. If I cut and paste a mouse section into the xorg.conf it hangs on boot and I have to REISUO.

---

### Post by gspat on 2009-12-24
I had the same issue with 9.10 n a few computers using both nVidia and ATI...

always went to the cli first boot (or after kernal update).

The simplest solution is to go get a copy of the video driver from the manufacturer's website and install it from the recovery shell using sudo ./NVIDIA-whatever.run or sudo ./ATI-whatever.run

In both cases, let it make a new xorg.conf file as it runs...

works like a dream after that.

hope this helps!

---

### Post by ST3ALTHPSYCH0 on 2009-12-25
I'll give that a try.

---

### Post by ST3ALTHPSYCH0 on 2009-12-30
Wow,I ran dpkg (I just thought it would be a good idea, no better reason), and now I'm getting this error
```

segmentation error
mountall: invalid option: --tmptime=0
Try 'mountall --help' for more information.
init: mountall main process (256) terminated with status 1
General error mounting filesystems
A maintenance shell will now be started

```I did check, and my /home partition isn't mounting, but I can mount it manually. Also, my 9.04 and UE 2.5 installs boot fine using the same /home partition. I set out to do some alpha testing and so far haven't been able to spend a solid hour in Lucid!

---

