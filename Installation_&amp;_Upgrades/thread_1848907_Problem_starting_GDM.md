---
title: "Problem starting GDM"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by pethor on 2011-09-23
Hey guys!

I really really want to install Ubuntu 11.04 on my laptop because my Windows is slowing down more and more. Therefore I downloaded the 32bit version of Ubuntu and tried to install it. 
I had to boot in secure graphics mode (or something like that) and now, right after installing, the GDE doesn't show up - instead a kind of commandline window appears and i have to enter username and password. 
It's like a full-screen terminal. When I try running ```
startx
``` or ```
xinit
``` I get following error message
```

X.Org X Server 1.10.1
X Protocol Version 11, Revision 0
Build Operating System Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=72A2061BA205E487 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date 19 April 2011 03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.20.2
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 23 16:44:53 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) VESA: Kernel modsetting driver in use, refusing to load
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
at http://wiki.x.org
for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server_error

```

Any help is appreciated.

Greetings,
Pethor

---

### Post by MAFoElffen on 2011-09-23
> **pethor said:**
> Hey guys!

I really really want to install Ubuntu 11.04 on my laptop because my Windows is slowing down more and more. Therefore I downloaded the 32bit version of Ubuntu and tried to install it. 
I had to boot in secure graphics mode (or something like that) and now, right after installing, the [COLOR=DarkOrange]GD[COLOR=Red][COLOR=DarkOrange]M[/COLOR][/COLOR] doesn't show up[/COLOR] - instead a kind of commandline window appears and i have to enter username and password. 
It's like a full-screen terminal. When I try running ```
startx
``` or ```
xinit
``` I get following error message
```

X.Org X Server 1.10.1
X Protocol Version 11, Revision 0
Build Operating System Linux [COLOR=Red]2.6.24-29-server i686 Ubuntu[/COLOR]
Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[COLOR=RoyalBlue]Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=72A2061BA205E487 loop=/ubuntu/disks/root.disk ro quiet splash[/COLOR]
Build Date 19 April 2011 03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.20.2
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 23 16:44:53 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
[COLOR=Red](EE) VESA: Kernel modsetting driver in use, refusing to load
(EE) No devices detected.[/COLOR]

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
at http://wiki.x.org
for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server_error

```Any help is appreciated.

Greetings,
Pethor
Backup a little fitst... Take a deep breath.

Now-  You are not using any Kernel boot switches on startup.  If your laptop has an NVida are Radeon GPU, it needs a boot switch to turn off KMS just to be able to load the VESA driver (as these 2 GPU's don't support vesa natively without being in that mode...)  Those switches would be "nomodeset" for NVidia or "radeon.mode=0" for ATI...

Next, "GDM" is starts differently in 11.04 on....  The X-Session is started by upstart services, so:
```

sudo service gdm start

```I guess the first bit of info we need from you is for you to post the results of
```

lspci -nn | grep VGA

```So we can start to figure this out with you...

---

### Post by oldos2er on 2011-09-23
> **pethor said:**
> I really really want to install Ubuntu 11.04 on my laptop because my Windows is slowing down more and more. Therefore I downloaded the 32bit version of Ubuntu and tried to install it. 
I had to boot in secure graphics mode (or something like that) and now, right after installing, the GDE doesn't show up - instead a kind of commandline window appears and i have to enter username and password. 
It's like a full-screen terminal. When I try running ```
startx
``` or ```
xinit
``` I get following error message
[CODE]
X.Org X Server 1.10.1
X Protocol Version 11, Revision 0
Build Operating System Linux 2.6.24-29-server i686 Ubuntu

You installed the server version, which has no X or GUI. Download the desktop version of Ubuntu instead. [http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest)

---

### Post by MAFoElffen on 2011-09-23
> **oldos2er said:**
> You installed the server version, which has no X or GUI. Download the desktop version of Ubuntu instead. [http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest)
Good catch (I missed that). ::embarassed::

Fresh Reinstall Desktop version would be best... or quick-fix would be 
```

sudo apt-get install ubuntu-desktop

```

---

### Post by pethor on 2011-09-24
Wait a sec guys!

I have downloaded the file: ubuntu-11.04-desktop-amd64.iso !

I assume this is NOT the server version :)

What shall I do now? A good friend of mine suggested to wait until release of Ubuntu 11.10.

Greetings,
Pethor

---

### Post by pethor on 2011-09-24
Maybe the output of this file helps, too:

> [  2468.505] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  2468.514] X Protocol Version 11, Revision 0
[  2468.516] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  2468.517] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  2468.519] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=72A2061BA205E487 loop=/ubuntu/disks/root.disk ro quiet splash
[  2468.521] Build Date: 19 April 2011  03:33:17PM
[  2468.522] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  2468.524] Current version of pixman: 0.20.2
[  2468.526] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  2468.529] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2468.535] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 23 17:24:04 2011
[  2468.537] (==) Using config file: "/etc/X11/xorg.conf"
[  2468.539] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2468.541] (==) No Layout section.  Using the first Screen section.
[  2468.541] (**) |-->Screen "Default Screen" (0)
[  2468.541] (**) |   |-->Monitor "Configured Monitor"
[  2468.541] (**) |   |-->Device "Configured Video Device"
[  2468.541] (==) Automatically adding devices
[  2468.541] (==) Automatically enabling devices
[  2468.541] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2468.541] 	Entry deleted from font path.
[  2468.542] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2468.542] 	Entry deleted from font path.
[  2468.542] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2468.542] 	Entry deleted from font path.
[  2468.542] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2468.542] 	Entry deleted from font path.
[  2468.542] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2468.542] 	Entry deleted from font path.
[  2468.542] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2468.542] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2468.542] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2468.542] (II) Loader magic: 0x81ffde0
[  2468.542] (II) Module ABI versions:
[  2468.542] 	X.Org ANSI C Emulation: 0.4
[  2468.542] 	X.Org Video Driver: 10.0
[  2468.542] 	X.Org XInput driver : 12.3
[  2468.542] 	X.Org Server Extension : 5.0
[  2468.543] (--) PCI:*(0:1:0:0) 10de:0ca9:1179:ff50 rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[  2468.543] (II) Open ACPI successful (/var/run/acpid.socket)
[  2468.543] (II) LoadModule: "extmod"
[  2468.543] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2468.543] (II) Module extmod: vendor="X.Org Foundation"
[  2468.543] 	compiled for 1.10.1, module version = 1.0.0
[  2468.543] 	Module class: X.Org Server Extension
[  2468.543] 	ABI class: X.Org Server Extension, version 5.0
[  2468.543] (II) Loading extension MIT-SCREEN-SAVER
[  2468.543] (II) Loading extension XFree86-VidModeExtension
[  2468.543] (II) Loading extension XFree86-DGA
[  2468.543] (II) Loading extension DPMS
[  2468.543] (II) Loading extension XVideo
[  2468.543] (II) Loading extension XVideo-MotionCompensation
[  2468.543] (II) Loading extension X-Resource
[  2468.543] (II) LoadModule: "dbe"
[  2468.543] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2468.543] (II) Module dbe: vendor="X.Org Foundation"
[  2468.543] 	compiled for 1.10.1, module version = 1.0.0
[  2468.543] 	Module class: X.Org Server Extension
[  2468.543] 	ABI class: X.Org Server Extension, version 5.0
[  2468.543] (II) Loading extension DOUBLE-BUFFER
[  2468.543] (II) LoadModule: "glx"
[  2468.544] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2468.544] (II) Module glx: vendor="X.Org Foundation"
[  2468.544] 	compiled for 1.10.1, module version = 1.0.0
[  2468.544] 	ABI class: X.Org Server Extension, version 5.0
[  2468.544] (==) AIGLX enabled
[  2468.544] (II) Loading extension GLX
[  2468.544] (II) LoadModule: "record"
[  2468.544] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2468.544] (II) Module record: vendor="X.Org Foundation"
[  2468.544] 	compiled for 1.10.1, module version = 1.13.0
[  2468.544] 	Module class: X.Org Server Extension
[  2468.544] 	ABI class: X.Org Server Extension, version 5.0
[  2468.544] (II) Loading extension RECORD
[  2468.544] (II) LoadModule: "dri"
[  2468.544] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2468.544] (II) Module dri: vendor="X.Org Foundation"
[  2468.544] 	compiled for 1.10.1, module version = 1.0.0
[  2468.544] 	ABI class: X.Org Server Extension, version 5.0
[  2468.544] (II) Loading extension XFree86-DRI
[  2468.544] (II) LoadModule: "dri2"
[  2468.544] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2468.544] (II) Module dri2: vendor="X.Org Foundation"
[  2468.544] 	compiled for 1.10.1, module version = 1.2.0
[  2468.544] 	ABI class: X.Org Server Extension, version 5.0
[  2468.544] (II) Loading extension DRI2
[  2468.544] (II) LoadModule: "vesa"
[  2468.545] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2468.545] (II) Module vesa: vendor="X.Org Foundation"
[  2468.545] 	compiled for 1.10.0, module version = 2.3.0
[  2468.545] 	Module class: X.Org Video Driver
[  2468.545] 	ABI class: X.Org Video Driver, version 10.0
[  2468.545] (II) VESA: driver for VESA chipsets: vesa
[  2468.545] (--) using VT number 7

[  2468.551] (EE) VESA: Kernel modesetting driver in use, refusing to load
[  2468.551] (WW) Falling back to old probe method for vesa
[  2468.551] (EE) No devices detected.
[  2468.551] 
Fatal server error:
[  2468.551] no screens found
[  2468.551] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  2468.551] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2468.551] 


---

### Post by oldos2er on 2011-09-24
What are your hardware specs? Did you run the commands MAFoElffen gave you, and can we see the output?

Also did you check the *.iso file or CD?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by MAFoElffen on 2011-09-24
> **oldos2er said:**
> What are your hardware specs? Did you run the commands MAFoElffen gave you, and can we see the output?

Also did you check the *.iso file or CD?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
I looked back through the Xorg.0.log... it matches what was there...  oldos2er caught me up with a little distraction-- and here is what was distracting with it --> 

 - The version of xorg-server was compiled originally (before packaging for Ubuntu) using a Linux server kernel, Linux 2.6.24-29-server i686 Ubuntu (normal and fine)...
 - The next line in the log is the current kernel version, Linux ubuntu 2.6.38-8-generic, that it is running on...
 - The next line is the kernel boot line, which is default with no special switches.

Yes  @both. I gave him a lspci commandline to figure out what video hardware he has using.  Without it, I gave him 2 different examples based on 2 common GPU's.  Reason for all that is the xorg error...

It says the VESA module cannot load concurrent with KMS loaded.  Solution- turn off kms.  Twist- Doing that in practice is different for each GPU and requires a unique kernel boot switch for each type...

So yes--> waiting on info and feedback.  With that feedback, we can either get the VESA driver working for him, or to see if he can be "better" supported with a specific driver for his specific GPU.

Sidenote- "GDE" as referenced here is actually / technically a package / service called "GDM."

---

### Post by oldos2er on 2011-09-24
Fixed thread title. Thanks MAFoElffen.

---

### Post by MAFoElffen on 2011-09-24
> **oldos2er said:**
> Fixed thread title. Thanks MAFoElffen.
LOL > Offtopic (sorry), but your (oldos2er) avatar looks exactly like one of my cats!  A 25 pound lap-kitty, who loves it when I'm online...

---

