---
title: "Unable to upgrade ubuntu from 11.04 to 11.10"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Aleck Agakhan on 2011-10-13
I have tried to upgrade ubuntu from 11.04 to 11.10 several times but always fail. This is the description of what I actually do:
I run "Update Manager" and it warns me that "Not all updates can be installed", if I press the button "Partial Upgrade" it asks me for password and when I enter it, the manager just disappears. So I press the button "Close" and then press the button "Upgrade" which is opposite the label "New Ubuntu release '11.10' is available". The manager shows the "release notes", after "downloading the release update tool" the window "Distribution Upgrade" appears with the list of stages. After "calculating the changes" in the stage "Setting new software channels" the window "Distribution Upgrade" just disappears.

In the next try I press the button "Install updates" instead of "Upgrade". The manager downloads more than 400M of different packages and then the window "Package operation failed" with the message "The installation or removal of a software package failed." emergs and there is also the message "installArchives() failed: " in the textbox "Details".

What's wrong with my system? And how do I upgrade it?

---

### Post by zvacet on 2011-10-13
Before you do upgrade be sure that your system is up-to-date.In terminal

```
sudo apt-get update && sudo apt-get upgrade
```

If you get any errors post them here.

---

### Post by Aleck Agakhan on 2011-10-13
"sudo apt-get upgrade" results in the error:
E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
I upgraded the package 'util-linux' via Synaptic and ran the command "sudo apt-get upgrade" again; it's working. I will tell the result.

---

### Post by cabotcat on 2011-10-13
I too had this problem through update manager. I simply downloaded the ISO and ran it from my DVD-Rom. Installed without incident.

---

### Post by vrraghy on 2011-10-13
> **zvacet said:**
> Before you do upgrade be sure that your system is up-to-date.In terminal

```
sudo apt-get update && sudo apt-get upgrade
```

If you get any errors post them here.
upgrade without update ubuntu problem

Hi zvacet,
Am on 11.04 right now and by mistake I went for an upgrade without doing an update.
Now an able to do neither. Please help.
Thanks in advance...! :)

---

### Post by Aleck Agakhan on 2011-10-13
Manual upgrade of 'util-linux' helped. But there was another problem after I had restarted my computer: X couldn't start and therefore gdm couldn't start and therefore I was left with bare console.
Here is the log from /var/log/Xorg.0.log
```

[    21.824] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.824] X Protocol Version 11, Revision 0
[    21.824] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.824] Current Operating System: Linux aleck 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686
[    21.824] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=68bce32c-d0b6-465a-b7ff-76bb7718f7b4 ro quiet splash vt.handoff=7
[    21.824] Build Date: 11 August 2011  03:47:56PM
[    21.824] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.824] Current version of pixman: 0.22.2
[    21.824] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    21.824] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.825] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Oct 13 22:21:56 2011
[    21.825] (==) Using config file: "/etc/X11/xorg.conf"
[    21.825] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.825] (==) ServerLayout "Layout0"
[    21.825] (**) |-->Screen "Screen0" (0)
[    21.825] (**) |   |-->Monitor "Monitor0"
[    21.825] (**) |   |-->Device "Device0"
[    21.825] (**) Option "Xinerama" "0"
[    21.825] (==) Automatically adding devices
[    21.825] (==) Automatically enabling devices
[    21.825] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.826] 	Entry deleted from font path.
[    21.826] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.826] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.826] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.826] (II) Loader magic: 0x81ffde0
[    21.826] (II) Module ABI versions:
[    21.826] 	X.Org ANSI C Emulation: 0.4
[    21.826] 	X.Org Video Driver: 10.0
[    21.826] 	X.Org XInput driver : 12.3
[    21.826] 	X.Org Server Extension : 5.0
[    21.826] (--) PCI:*(0:2:0:0) 10de:0402:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x00009000/128, BIOS @ 0x????????/131072
[    21.827] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.827] (II) LoadModule: "extmod"
[    21.827] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.827] (II) Module extmod: vendor="X.Org Foundation"
[    21.827] 	compiled for 1.10.1, module version = 1.0.0
[    21.827] 	Module class: X.Org Server Extension
[    21.827] 	ABI class: X.Org Server Extension, version 5.0
[    21.827] (II) Loading extension MIT-SCREEN-SAVER
[    21.827] (II) Loading extension XFree86-VidModeExtension
[    21.827] (II) Loading extension XFree86-DGA
[    21.827] (II) Loading extension DPMS
[    21.827] (II) Loading extension XVideo
[    21.827] (II) Loading extension XVideo-MotionCompensation
[    21.827] (II) Loading extension X-Resource
[    21.827] (II) LoadModule: "dbe"
[    21.828] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.828] (II) Module dbe: vendor="X.Org Foundation"
[    21.828] 	compiled for 1.10.1, module version = 1.0.0
[    21.828] 	Module class: X.Org Server Extension
[    21.828] 	ABI class: X.Org Server Extension, version 5.0
[    21.828] (II) Loading extension DOUBLE-BUFFER
[    21.828] (II) LoadModule: "glx"
[    21.828] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.828] (II) Module glx: vendor="X.Org Foundation"
[    21.828] 	compiled for 1.10.1, module version = 1.0.0
[    21.828] 	ABI class: X.Org Server Extension, version 5.0
[    21.828] (==) AIGLX enabled
[    21.828] (II) Loading extension GLX
[    21.828] (II) LoadModule: "record"
[    21.829] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.829] (II) Module record: vendor="X.Org Foundation"
[    21.829] 	compiled for 1.10.1, module version = 1.13.0
[    21.829] 	Module class: X.Org Server Extension
[    21.829] 	ABI class: X.Org Server Extension, version 5.0
[    21.829] (II) Loading extension RECORD
[    21.829] (II) LoadModule: "dri"
[    21.829] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.829] (II) Module dri: vendor="X.Org Foundation"
[    21.829] 	compiled for 1.10.1, module version = 1.0.0
[    21.829] 	ABI class: X.Org Server Extension, version 5.0
[    21.829] (II) Loading extension XFree86-DRI
[    21.829] (II) LoadModule: "dri2"
[    21.830] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.830] (II) Module dri2: vendor="X.Org Foundation"
[    21.830] 	compiled for 1.10.1, module version = 1.2.0
[    21.830] 	ABI class: X.Org Server Extension, version 5.0
[    21.830] (II) Loading extension DRI2
[    21.830] (II) LoadModule: "nvidia"
[    21.830] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    21.830] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.830] 	compiled for 4.0.2, module version = 1.0.0
[    21.830] 	Module class: X.Org Video Driver
[    21.831] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[    21.831] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.831] (--) using VT number 1

[    21.834] (II) Loading sub module "fb"
[    21.834] (II) LoadModule: "fb"
[    21.834] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.834] (II) Module fb: vendor="X.Org Foundation"
[    21.834] 	compiled for 1.10.1, module version = 1.0.0
[    21.834] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.834] (II) Loading sub module "wfb"
[    21.834] (II) LoadModule: "wfb"
[    21.835] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.835] (II) Module wfb: vendor="X.Org Foundation"
[    21.835] 	compiled for 1.10.1, module version = 1.0.0
[    21.835] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.835] (II) Loading sub module "ramdac"
[    21.835] (II) LoadModule: "ramdac"
[    21.835] (II) Module "ramdac" already built-in
[    21.835] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    21.835] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.835] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.835] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.835] (==) NVIDIA(0): RGB weight 888
[    21.835] (==) NVIDIA(0): Default visual is TrueColor
[    21.835] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.835] (**) NVIDIA(0): Option "TwinView" "0"
[    21.835] (**) NVIDIA(0): Option "MetaModes" "1280x960_85 +0+0"
[    21.835] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    21.835] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    21.835] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    21.835] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    21.835] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.
[    22.383] (EE) NVIDIA(0): The interrupt for the NVIDIA GPU at PCI:2:0:0 appears to be
[    22.383] (EE) NVIDIA(0):     edge-triggered.  Please see Chapter 8: Common Problems in
[    22.383] (EE) NVIDIA(0):     the README for additional information.
[    22.383] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    22.383] (II) UnloadModule: "nvidia"
[    22.383] (II) Unloading nvidia
[    22.383] (II) UnloadModule: "wfb"
[    22.383] (II) Unloading wfb
[    22.383] (II) UnloadModule: "fb"
[    22.383] (II) Unloading fb
[    22.383] (EE) Screen(s) found, but none have a usable configuration.
[    22.383] 
Fatal server error:
[    22.383] no screens found
[    22.383] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    22.383] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    22.383] 
[    22.389]  ddxSigGiveUp: Closing log

```

---

### Post by geisslab on 2011-10-13
I'm running into a similar error while trying to upgrade to ubuntu 11.10. my error while installing
details: installArchives () failed:
So then I tried this 

 sudo apt-get update && sudo apt-get upgrade

And got the following

Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
E: Problem executing scripts APT::Update::Post-Invoke-Success 'touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true'
E: Sub-process returned an error code


I'm very new to ubuntu, so I'm not sure if this error is the same or just similar to what the others are having.

Thank you for your help

---

### Post by zvacet on 2011-10-13
@ **vrraghy**

In terminal 

```
sudo apt-get update && sudo apt-get upgrade
```

Post output of this commands to make easier others to help you.

---

### Post by vrraghy on 2011-10-14
Hi,

I executed the same command,
i.e. "sudo apt-get update && sudo apt-get upgrade"
and got the following:

```

Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Hit http://archive.canonical.com oneiric Release.gpg
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Ign http://us.archive.ubuntu.com oneiric-security InRelease                   
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease
Hit http://us.archive.ubuntu.com oneiric Release.gpg                 
Hit http://archive.canonical.com oneiric Release                     
Hit http://extras.ubuntu.com oneiric Release                         
Get:2 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg
Get:3 http://us.archive.ubuntu.com oneiric-proposed Release.gpg [198 B]
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://us.archive.ubuntu.com oneiric Release
Get:4 http://us.archive.ubuntu.com oneiric-updates Release [24.2 kB]           
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric-security Release            
Get:5 http://us.archive.ubuntu.com oneiric-proposed Release [28.2 kB]          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources             
Hit http://us.archive.ubuntu.com oneiric/universe Sources               
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Get:6 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [14 B]
Get:7 http://us.archive.ubuntu.com oneiric-updates/main Sources [2,033 B]
Get:8 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [14 B]   
Get:9 http://us.archive.ubuntu.com oneiric-updates/universe Sources [1,361 B]  
Get:10 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [5,297 B]
Get:11 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [14 B]
Get:12 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [14 B]
Get:13 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [1,975 B]
Get:14 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [72 B]
Get:15 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [70 B]
Get:16 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [70 B]
Get:17 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [72 B]
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources 
Hit http://us.archive.ubuntu.com oneiric-security/main Sources       
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources 
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources   
Hit http://us.archive.ubuntu.com oneiric-security/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages
Ign http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Get:18 http://us.archive.ubuntu.com oneiric-proposed/restricted Sources [14 B]
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Get:19 http://us.archive.ubuntu.com oneiric-proposed/main Sources [21.8 kB]
Get:20 http://us.archive.ubuntu.com oneiric-proposed/multiverse Sources [14 B] 
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Get:21 http://us.archive.ubuntu.com oneiric-proposed/universe Sources [1,886 B]
Get:22 http://us.archive.ubuntu.com oneiric-proposed/restricted amd64 Packages [14 B]
Get:23 http://us.archive.ubuntu.com oneiric-proposed/main amd64 Packages [49.2 kB]
Get:24 http://us.archive.ubuntu.com oneiric-proposed/multiverse amd64 Packages [14 B]
Get:25 http://us.archive.ubuntu.com oneiric-proposed/universe amd64 Packages [10.5 kB]
Get:26 http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex [73 B]
Get:27 http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex [70 B]
Get:28 http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex [70 B]
Get:29 http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex [72 B]
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Get:30 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [3,044 B]
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:31 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [1,474 B]
Get:32 http://us.archive.ubuntu.com oneiric-proposed/main Translation-en [25.4 kB]
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en
Get:33 http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en [6,427 B]
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://us.archive.ubuntu.com oneiric-security/main Translation-en_US       
Ign http://us.archive.ubuntu.com oneiric-security/main Translation-en          
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en    
Ign http://us.archive.ubuntu.com oneiric-security/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com oneiric-security/restricted Translation-en    
Ign http://us.archive.ubuntu.com oneiric-security/universe Translation-en_US   
Ign http://us.archive.ubuntu.com oneiric-security/universe Translation-en      
Fetched 184 kB in 8s (22.6 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot alsa-utils appmenu-gtk apport-gtk apt apt-transport-https apt-utils aptdaemon apturl
  apturl-common at-spi audacity audacity-data awn-applet-indicator bamfdaemon banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab bind9-host binutils
  bogofilter-bdb brasero brasero-cdrkit brasero-common brltty brltty-x11 ca-certificates calibre
  calibre-bin cdrdao checkbox checkbox-gtk cheese cheese-common chromium-browser chromium-browser-l10n
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main compizconfig-backend-gconf
  computer-janitor computer-janitor-gtk console-setup cpp cpp-4.5 dnsutils doc-base easystroke eclipse-jdt
  eclipse-pde eclipse-platform eclipse-platform-data eclipse-rcp empathy empathy-common eog evince
  evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-exchange evolution-indicator evolution-plugins evolution-webcal file-roller filezilla
  filezilla-common firefox firefox-globalmenu flashplugin-installer g++ g++-4.5 gbrainy gcalctool gcc
  gcc-4.5 gcc-4.5-base gcj-4.5-jre-lib gconf-editor gdm gedit gedit-common geoclue-ubuntu-geoip
  gir1.2-appindicator-0.1 gir1.2-dbusmenu-glib-0.4 gir1.2-freedesktop gir1.2-glib-2.0 glib-networking
  gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-disk-utility
  gnome-games-common gnome-icon-theme gnome-keyring gnome-mahjongg gnome-media gnome-nettool gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool
  gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon
  gnome-sudoku gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-user-share gnome-utils-common gnomine gnupg-agent gnupg2 gramps grub-common grub-pc
  gsettings-desktop-schemas gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs
  gvfs-backends gvfs-fuse gwibber gwibber-service ia32-libs ibus ibus-gtk ibus-pinyin
  ibus-pinyin-db-android icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  indicator-application indicator-appmenu indicator-datetime indicator-messages indicator-session
  indicator-sound info iproute iputils-ping jockey-common jockey-gtk language-selector-common
  language-selector-gnome lib32asound2 lib32gcc1 lib32ncurses5 lib32ncursesw5 lib32stdc++6
  libalgorithm-diff-xs-perl libapparmor-perl libappindicator0.1-cil libappindicator1 libapt-pkg-perl
  libart2.0-cil libasound2 libasound2-plugins libawn1 libbamf0 libbind9-60 libc-bin libc-dev-bin libc6
  libc6-dev libc6-i386 libcairo-perl libcanberra-pulse libcanberra0 libcloog-ppl0 libcompizconfig0
  libcurl3 libdecoration0 libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib
  libdesktop-agnostic-vfs-gio libdesktop-agnostic0 libdigest-sha1-perl libdns69 libept1
  libequinox-osgi-java libevolution libgail-common libgail18 libgcc1 libgcj-bc libgcj11 libgconf2.0-cil
  libgdata1.7-cil libgdu-gtk0 libgfortran3 libgirepository-1.0-1 libgkeyfile1.0-cil libgl1-mesa-dri
  libgl1-mesa-glx libglade2.0-cil libglib-perl libglib2.0-0 libglib2.0-bin libglib2.0-cil
  libglibmm-2.4-1c2a libgmime2.4-cil libgmpxx4ldbl libgnome-bluetooth8 libgnome-keyring0
  libgnome-vfs2.0-cil libgnome2.24-cil libgnomekbd-common libgomp1 libgtk-sharp-beans-cil libgtk-vnc-1.0-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkmm-2.4-1c2a libgucharmap7 libgudev1.0-cil
  libhighgui2.1 libhtml-parser-perl libindicate5 libio-pty-perl libisc62 libisccfg62 libisofs6
  libjack-jackd2-0 liblapack3gf liblaunchpad-integration1.0-cil liblocale-gettext-perl liblucene2-java
  liblwres60 libmagick++3 libmission-control-plugins0 libmlt++3 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-corlib2.0-cil libmono-management2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libmono-zeroconf1.0-cil libmpc2
  libmpfr4 libmusicbrainz4c2a libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libnet-dbus-perl libnet-dns-perl libnm-glib-vpn1 libnotify0.4-cil libpam-modules
  libpam-modules-bin libpango-perl libphonon4 libplymouth2 libpulse-mainloop-glib0 libpulse0 libpurple0
  libpython2.7 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 librdf0 libreadline6 libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math libreoffice-writer
  librsvg2-2 librsvg2-common libsasl2-2 libsasl2-modules libsigc++-2.0-0c2a libsnmp15
  libstartup-notification0 libstdc++6 libstdc++6-4.5-dev libsub-name-perl libsyncdaemon-1.0-1
  libtag1-vanilla libtag1c2a libtaglib2.0-cil libtelepathy-logger2 libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libubuntuone-1.0-1 libubuntuone1.0-cil libunity-2d-private0
  libuuid-perl libv4l-0 libvte-common libvte9 libwpd-0.9-9 libwps-0.2-2 libwww-perl libxapian22
  libxml-parser-perl libzrtpcpp-1.4-0 light-themes lintian linux-generic linux-headers-generic
  linux-image-generic melt menu mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mount
  mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share ncurses-bin
  network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notify-osd
  nspluginwrapper ntfs-3g openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client openssl
  overlay-scrollbar parted perl perl-base perl-modules phonon pidgin pidgin-data pidgin-libnotify plymouth
  plymouth-label protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python python-appindicator python-apt
  python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets
  python-awn python-crypto python-desktop-agnostic python-evolution python-gconf python-glade2
  python-gnome2 python-gobject python-gtk2 python-ibus python-indicate python-minimal python-mlt3
  python-openssl python-protobuf python-pyatspi python-pythonmagick python-tagpy python-ubuntuone-client
  python-ubuntuone-control-panel python-uno python-vte python-xapian python2.7 python2.7-minimal rdesktop
  sat4j seahorse shotwell simple-scan software-center software-properties-gtk stellarium supertuxkart
  supertuxkart-data synaptic tcl tcpdump telepathy-idle telepathy-logger telepathy-mission-control-5
  tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk twinkle
  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk unity
  unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-common
  unity-place-applications unity-place-files update-manager update-manager-core update-notifier
  update-notifier-common upower usb-creator-common usb-creator-gtk vim-common vim-tiny vinagre vino
  virtualbox-ose virtualbox-ose-dkms virtualbox-ose-qt vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse wget
  wine wine1.2 wireshark wireshark-common wpasupplicant xchat xchat-common xserver-xorg-core
  xserver-xorg-video-intel yelp zenity
The following packages will be upgraded:
  acpid alacarte alsa-base ant ant-optional app-install-data app-install-data-partner apparmor
  apparmor-utils appmenu-qt apport apport-symptoms apt-xapian-index aptdaemon-data aspell-en at
  avahi-autoipd avahi-daemon avahi-utils avant-window-navigator avant-window-navigator-data
  awn-applet-animal-farm awn-applet-awn-notification-daemon awn-applet-awn-system-monitor
  awn-applet-awnterm awn-applet-bandwidth-monitor awn-applet-battery-applet awn-applet-cairo-clock
  awn-applet-cairo-main-menu awn-applet-comics awn-applet-common-folder awn-applet-cpufreq
  awn-applet-dialect awn-applet-feeds awn-applet-file-browser-launcher awn-applet-garbage
  awn-applet-hardware-sensors awn-applet-mail awn-applet-media-control awn-applet-media-icon-applet
  awn-applet-media-player awn-applet-notification-area awn-applet-quit-applet awn-applet-related
  awn-applet-shinyswitcher awn-applet-showdesktop awn-applet-stack awn-applet-thinkhdaps awn-applet-todo
  awn-applet-volume-control awn-applet-weather awn-applet-webapplet awn-applets-common awn-settings
  base-files base-passwd bash bash-completion binfmt-support bluez bluez-alsa bluez-cups bluez-gstreamer
  bogofilter bogofilter-common bsdmainutils bsdutils busybox-initramfs busybox-static bzr bzrtools
  ca-certificates-java cabextract chromium-codecs-ffmpeg cli-common command-not-found
  command-not-found-data compizconfig-settings-manager consolekit cron cups cups-bsd cups-client
  cups-common cups-driver-gutenprint cups-ppdc dash dbus dbus-x11 debconf debconf-i18n debianutils
  default-jre default-jre-headless desktop-file-utils dictionaries-common dkms dmsetup dnsmasq-base
  dosfstools dpkg dpkg-dev dvd+rw-tools eject espeak espeak-data example-content fakeroot file
  firefox-gnome-support firefox-locale-en fontconfig fontconfig-config foo2zjs foomatic-db-compressed-ppds
  foomatic-db-engine foomatic-filters friendly-recovery ftp furiusisomount fuse-utils fuseiso9660 gamin
  gcj-4.5-base gconf-defaults-service gconf2 gconf2-common gdb gdm-guest-session geoclue geoip-database
  ghostscript ghostscript-cups ghostscript-x gimp gimp-data gir1.2-atk-1.0 gir1.2-dee-0.5 gir1.2-gconf-2.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gtk-2.0 gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-soup-2.4
  gnome-accessibility-themes gnome-activity-journal gnome-codec-install gnome-doc-utils gnome-menus
  gnome-user-guide gpdftext graphviz grep groff-base growisofs grub-gfxpayload-lists gsfonts-x11
  gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-tools gstreamer0.10-x gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hal hdparm homebank homebank-data hostname hpijs hplip hplip-cups hplip-data
  humanity-icon-theme hunspell-en-ca hunspell-en-us hwdata ibus-table icedtea6-plugin icoutils ifupdown
  im-switch imagemagick initramfs-tools initramfs-tools-bin initscripts inputattach insserv install-info
  iputils-arping iputils-tracepath isc-dhcp-client isc-dhcp-common iso-codes isomaster jarwrapper
  java-common kbd kerneloops-daemon keyboard-configuration klibc-utils language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base launchpad-integration less lftp
  liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni libacl1 libao-common libao4 libapparmor1
  libasm3-java libass4 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatspi1.0-0 libattr1 libaudio2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0
  libavahi-ui0 libblas3gf libblkid1 libbluetooth3 libbrlapi0.5 libbsd0 libburn4 libc-ares2 libcaca0
  libcairo-gobject2 libcairo2 libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcap-ng0 libcap2
  libcap2-bin libcdaudio1 libcdt4 libcgraph5 libck-connector0 libcolamd2.7.1 libcommons-codec-java
  libcommons-collections3-java libcommons-httpclient-java libcups2 libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3-gnutls libcv2.1 libcvaux2.1 libdatrie1 libdb4.8
  libdbus-1-3 libdbus-glib-1-2 libdbusmenu-qt2 libdc1394-22 libdca0 libdconf0 libdee-1.0-1
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdigest-hmac-perl libdirac-encoder0 libdirectfb-1.2-9
  libdjvulibre-text libdjvulibre21 libdpkg-perl libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2
  libdv4 libdvdread4 libebml3 libecj-java libedit2 libelf1 libelfg0 libenca0 libenchant1c2a libespeak1
  libevent-1.4-2 libexif12 libfftw3-3 libflac++6 libflac8 libfontconfig1 libfreetype6 libfuse2 libgadu3
  libgamin0 libgcj-common libgconf2-4 libgcrypt11 libgd2-xpm libgdata-common libgdbm3 libgdk-pixbuf2.0-0
  libgdu0 libgee2 libgeoclue0 libgeoip1 libgexiv2-0 libgimp2.0 libgksu2-0 libgladeui-1-11 libglew1.5
  libglewmx1.5 libglib2.0-data libglu1-mesa libgmime-2.4-2 libgmp3c2 libgnome-menu2 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnutls26
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpm2 libgpod-common libgpod4 libgraph4 libgs9
  libgs9-common libgsl0ldbl libgssapi-krb5-2 libgssdp-1.0-2 libgstfarsight0.10-0
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-common libgtkspell0 libgtop2-7
  libgtop2-common libgudev-1.0-0 libgupnp-1.0-3 libgupnp-igd-1.0-3 libgutenprint2 libgvc5 libgvpr1
  libgweather-common libhal-storage1 libhal1 libhpmud0 libhtml-format-perl libhtml-tree-perl libhttrack2
  libice6 libidl0 libidn11 libido-0.1-0 libieee1284-3 libimobiledevice2 libipc-run-perl libirrlicht1.7a
  libisccc60 libiw30 libjpeg62 libjs-jquery libjson-glib-1.0-0 libjtidy-java libk5crypto3 libkeyutils1
  libklibc libkpathsea5 libkrb5-3 libkrb5support0 libksba8 liblaunchpad-integration-common
  liblaunchpad-integration1 liblcms1 libldap-2.4-2 liblircclient0 liblouis-data liblouis2 libltdl7
  liblua5.1-0 liblvm2app2.2 liblzo2-2 libmagic1 libmagickcore3 libmagickcore3-extra libmagickwand3
  libmailtools-perl libmeanwhile1 libmetacity-private0 libmikmod2 libmimic0 libmlt-data libmms0 libmng1
  libmodplug1 libmono-cairo2.0-cil libmono-i18n-west2.0-cil libmtdev1 libmysqlclient16 libneon27-gnutls
  libnet-domain-tld-perl libnet-ip-perl libnewt0.52 libnih-dbus1 libnih1 libnl1 libnotify4 libnspr4
  libnss3 libnss3-1d libofx4 libogg0 libopenal1 libopencc1 liborbit2 liborc-0.4-0 libosp5
  libpam-ck-connector libpam-gnome-keyring libpam-runtime libpam0g libpango1.0-0 libpangomm-1.4-1
  libpaper-utils libpaper1 libparse-debianchangelog-perl libparted0debian1 libpathplan4 libpcap0.8 libpci3
  libpciaccess0 libpcsclite1 libpipeline1 libpixman-1-0 libplist1 libpng12-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-gtk-1-0 libpoppler-glib6 libpoppler13
  libportaudio2 libportsmf0 libproxy0 libpurple-bin libqt3-mt libqtassistantclient4 libqtbamf1 libqtdee2
  libqtwebkit4 libquvi0 libraptor1 libraw1394-11 libreoffice-emailmerge libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-l10n-common libreoffice-style-human librpc-xml-perl librtmp0
  libsamplerate0 libsane libsane-hpaio libschroedinger-1.0-0 libsdl-image1.2 libsdl-mixer1.2
  libsdl1.2debian libsdl1.2debian-pulseaudio libselinux1 libsensors4 libsepol1 libservlet2.5-java
  libsgutils2-2 libshout3 libslang2 libslf4j-java libsm6 libsmbclient libsmi2ldbl libsndfile1 libsnmp-base
  libsoundtouch0 libsoup-gnome2.4-1 libsoup2.4-1 libsox-fmt-alsa libsox-fmt-base libsox1b libspeechd2
  libspeex1 libspeexdsp1 libsqlite3-0 libssl0.9.8 libtalloc2 libtasn1-3 libtdb1 libtelepathy-farsight0
  libtelepathy-glib0 libthai-data libthai0 libtiff4 libtotem-plparser17 libts-0.0-0 libtwolame0 libudev0
  libunique-1.0-0 libunistring0 libupnp3 libupower-glib1 liburi-perl libusb-0.1-4 libusb-1.0-0 libuser1
  libutempter0 libutouch-frame1 libutouch-geis1 libutouch-grail1 libuuid1 libva-x11-1 libva1
  libvisual-0.4-plugins libvlc5 libvlccore4 libvncserver0 libvorbis0a libvorbisenc2 libvorbisfile3
  libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwildmidi1 libwireshark-data libwmf0.2-7
  libwmf0.2-7-gtk libwnck-common libwnck22 libwpg-0.2-2 libwrap0 libwxbase2.8-0 libwxgtk2.8-0 libx11-6
  libx11-data libx11-xcb1 libx86-1 libxau6 libxcb-dri2-0 libxcb-keysyms1 libxcb-randr0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext6 libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2
  libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxklavier16 libxml-twig-perl libxml2 libxml2-utils
  libxmu6 libxmuu1 libxp6 libxrandr2 libxrender1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxxf86vm1
  libzbar0 libzeitgeist-1.0-1 libzephyr4 linux-firmware linux-libc-dev linux-sound-base locales
  lockfile-progs login logrotate lsb-base lsb-release make man-db media-player-info memtest86+ metacity
  metacity-common mlocate mobile-broadband-provider-info modemmanager module-init-tools mountall mousepad
  mtr-tiny multiarch-support myspell-en-au myspell-en-gb myspell-en-za mysql-common mythes-en-us
  ncurses-base netbase netcat-openbsd ntpdate nux-tools nvidia-common obexd-client onboard
  openprinting-ppds openshot openshot-doc os-prober p7zip-full passwd patch pciutils
  phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4 pitivi pkg-config plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text pm-utils policykit-1 policykit-1-gnome policykit-desktop-privileges
  poppler-utils popularity-contest pppoeconf procps psmisc pxljr python-apport python-apt-common
  python-argparse python-avahi python-awn-extras python-beautifulsoup python-brlapi python-bzrlib
  python-cairo python-central python-chardet python-coherence python-compizconfig python-configglue
  python-configobj python-cssutils python-cups python-cupshelpers python-dateutil python-dbus
  python-debian python-django python-dnspython python-egenix-mxdatetime python-egenix-mxtools
  python-encutils python-farsight python-feedparser python-gdbm python-gmenu python-gnomedesktop
  python-gnomekeyring python-gnupginterface python-gobject-cairo python-gpod python-gst0.10
  python-gtksourceview2 python-gtkspell python-gtop python-httplib2 python-imaging python-keyring
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient python-lazr.uri
  python-libproxy python-libuser python-libxml2 python-louis python-lxml python-mako python-markupsafe
  python-mpd python-mutagen python-nevow python-notify python-numpy python-oauth python-oauth2
  python-papyon python-paramiko python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-pycurl python-pyinotify python-pypdf python-pysqlite2 python-qt4
  python-rsvg python-serial python-simplejson python-sip python-smbc python-software-properties
  python-speechd python-storm python-support python-telepathy python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-names python-twisted-web python-twisted-web2 python-tz
  python-ubuntuone-storageprotocol python-utidylib python-virtkey python-wadllib python-webkit
  python-webob python-wnck python-wsgi-intercept python-xdg python-xkit python-xklavier
  python-zope.interface q4wine readline-common rsync rsyslog rtkit samba samba-common samba-common-bin
  sane-utils screenlets screenlets-pack-all sed sessioninstaller sgml-data shared-mime-info smbclient
  speech-dispatcher splix sqlite3 squashfs-tools ssh-askpass-gnome stellarium-data strace sudo syslinux
  syslinux-common system-config-printer-common system-config-printer-gnome system-config-printer-udev
  sysv-rc sysvinit-utils tcpd telepathy-butterfly telepathy-gabble telepathy-haze telepathy-salut toshset
  tsconf ttf-dejavu-core ttf-dejavu-extra ttf-droid ttf-freefont ttf-liberation ttf-mscorefonts-installer
  ttf-opensymbol ttf-thai-tlwg ttf-ubuntu-font-family tzdata tzdata-java ubuntu-artwork ubuntu-docs
  ubuntu-minimal ubuntu-mono ubuntu-restricted-addons ubuntu-sso-client ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers ucf udev udisks ufw unattended-upgrades unity-asset-pool
  uno-libs3 update-inetd upstart ure usb-imagewriter usb-modeswitch usb-modeswitch-data usbutils
  util-linux uuid-runtime vlc-data webhttrack webhttrack-common whiptail whois wifi-radar winbind
  winetricks wireless-crda wireless-tools x-ttcidfont-conf x11-common x11-utils x11-xfs-utils
  x11-xkb-utils x11-xserver-utils xauth xdg-user-dirs xdg-user-dirs-gtk xdg-utils xfce-keyboard-shortcuts
  xfconf xfonts-utils xfwm4 xfwm4-themes xinit xkb-data xorg xorg-docs-core xscreensaver-data
  xscreensaver-gl xserver-common xserver-xorg xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-i128 xserver-xorg-video-mach64
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo xsltproc xterm
  xul-ext-ubufox yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zeitgeist-extension-fts zip
912 upgraded, 0 newly installed, 0 to remove and 496 not upgraded.
Need to get 15.1 MB/412 MB of archives.
After this operation, 121 MB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main cups amd64 1.5.0-8ubuntu2 [2,001 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcups2 amd64 1.5.0-8ubuntu2 [175 kB]    
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcupsmime1 amd64 1.5.0-8ubuntu2 [15.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcupsimage2 amd64 1.5.0-8ubuntu2 [53.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main cups-common all 1.5.0-8ubuntu2 [712 kB]   
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main cups-bsd amd64 1.5.0-8ubuntu2 [44.3 kB]   
Get:7 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main cups-client amd64 1.5.0-8ubuntu2 [166 kB] 
Get:8 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcupscgi1 amd64 1.5.0-8ubuntu2 [32.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcupsdriver1 amd64 1.5.0-8ubuntu2 [21.9 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libcupsppdc1 amd64 1.5.0-8ubuntu2 [54.7 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main cups-ppdc amd64 1.5.0-8ubuntu2 [33.5 kB] 
Get:12 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main libbluetooth3 amd64 4.96-0ubuntu4 [61.8 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main bluez amd64 4.96-0ubuntu4 [579 kB]       
Get:14 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main bluez-alsa amd64 4.96-0ubuntu4 [57.2 kB] 
Get:15 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main bluez-cups amd64 4.96-0ubuntu4 [24.1 kB] 
Get:16 http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed/main bluez-gstreamer amd64 4.96-0ubuntu4 [74.2 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libiw30 amd64 30~pre9-5ubuntu1 [20.4 kB]          
Get:18 http://us.archive.ubuntu.com/ubuntu/ oneiric/main wireless-tools amd64 30~pre9-5ubuntu1 [117 kB]    
Get:19 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe wifi-radar all 2.0.s08+dfsg-1 [50.4 kB]       
Get:20 http://us.archive.ubuntu.com/ubuntu/ oneiric/main wireless-crda amd64 1.14 [16.0 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ oneiric/main x-ttcidfont-conf all 32+nmu2 [20.2 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ oneiric/main x11-xfs-utils amd64 7.6+1 [27.1 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ oneiric/main x11-xserver-utils amd64 7.6+3 [182 kB]            
Get:24 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xdg-user-dirs amd64 0.14-0ubuntu1 [51.9 kB]       
Get:25 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xdg-user-dirs-gtk amd64 0.8-1ubuntu2 [11.3 kB]    
Get:26 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xfwm4 amd64 4.8.2-0ubuntu1 [1,150 kB]         
Get:27 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xfwm4-themes all 4.6.0-3 [554 kB]             
Get:28 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xinit amd64 1.3.1-1 [18.6 kB]                     
Get:29 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-r128 amd64 6.8.1-5 [56.0 kB]   
Get:30 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-mach64 amd64 6.9.0-1 [88.4 kB] 
Get:31 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-radeon amd64 1:6.14.99~git20110811.g93fc084-0ubuntu1 [451 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-ati amd64 1:6.14.99~git20110811.g93fc084-0ubuntu1 [6,778 B]
Get:33 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-neomagic amd64 1:1.2.5-2 [37.2 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-nouveau amd64 1:0.0.16+git20110411+8378443-1 [110 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-openchrome amd64 1:0.2.904+svn920-1 [178 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-qxl amd64 0.0.14-1 [66.2 kB]   
Get:37 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-s3 amd64 1:0.6.3-4 [35.5 kB]   
Get:38 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-siliconmotion amd64 1:1.7.5-1 [58.8 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-sis amd64 1:0.10.3-3 [275 kB]  
Get:40 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-sisusb amd64 1:0.9.4-2 [42.4 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-tdfx amd64 1:1.4.3-4 [38.2 kB] 
Get:42 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-trident amd64 1:1.3.4-2 [72.7 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-vesa amd64 1:2.3.0-7 [16.7 kB] 
Get:44 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-vmware amd64 1:11.0.3-2 [33.4 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-all amd64 1:7.6+7ubuntu7 [5,004 B]
Get:46 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-voodoo amd64 1:1.2.4-2 [18.5 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-tseng amd64 1:1.2.4-2 [27.8 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-s3virge amd64 1:1.10.4-4 [41.4 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-i128 amd64 1:1.3.4-2 [29.2 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-chips amd64 1:1.2.4-1 [72.4 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-ark amd64 1:0.7.3-2 [12.7 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xserver-xorg-video-apm amd64 1:1.2.3-2 [60.9 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-evdev amd64 1:2.6.0-1ubuntu13 [30.4 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-synaptics amd64 1.4.1-1ubuntu2 [66.7 kB]
Get:55 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-mouse amd64 1:1.7.1-1 [40.4 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-vmmouse amd64 1:12.7.0-2 [15.8 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-wacom amd64 1:0.11.0-0ubuntu2 [80.8 kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-all amd64 1:7.6+7ubuntu7 [4,912 B]
Get:59 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg amd64 1:7.6+7ubuntu7 [79.9 kB]       
Get:60 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xorg-docs-core all 1:1.6-1ubuntu2 [42.2 kB]       
Get:61 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xterm amd64 271-1ubuntu2 [564 kB]                 
Get:62 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xorg amd64 1:7.6+7ubuntu7 [2,704 B]               
Get:63 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xscreensaver-data amd64 5.14-1ubuntu1 [127 kB]    
Get:64 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xscreensaver-gl amd64 5.14-1ubuntu1 [483 kB]      
Get:65 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xserver-common all 2:1.10.4-1ubuntu4 [32.8 kB]    
Get:66 http://us.archive.ubuntu.com/ubuntu/ oneiric/main xul-ext-ubufox all 1.0-0ubuntu1 [48.6 kB]         
Get:67 http://us.archive.ubuntu.com/ubuntu/ oneiric/main yelp-xsl all 3.2.0-0ubuntu1 [285 kB]              
Get:68 http://us.archive.ubuntu.com/ubuntu/ oneiric/main zip amd64 3.0-4 [262 kB]                          
Get:69 http://us.archive.ubuntu.com/ubuntu/ oneiric/main aptdaemon-data all 0.43+bzr697-0ubuntu1 [163 kB]  
Get:70 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-compizconfig amd64 0.9.5.94-0ubuntu2 [104 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe compizconfig-settings-manager all 0.9.5.92-0ubuntu1 [1,209 kB]
Get:72 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe icedtea6-plugin all 6b21.1.3-1ubuntu1 [926 B] 
Get:73 http://us.archive.ubuntu.com/ubuntu/ oneiric/main inputattach amd64 1:1.4.1-1 [18.8 kB]             
Get:74 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libass4 amd64 0.9.13-1 [56.5 kB]              
Get:75 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libbrlapi0.5 amd64 4.2-8ubuntu5 [23.7 kB]         
Get:76 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libc-ares2 amd64 1.7.4-1 [36.4 kB]                
Get:77 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdc1394-22 amd64 2.1.3-4 [89.5 kB]              
Get:78 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libdca0 amd64 0.0.5-4 [109 kB]                
Get:79 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdconf0 amd64 0.10.0-0ubuntu1 [24.4 kB]         
Get:80 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgexiv2-0 amd64 0.3.1-0ubuntu2 [49.2 kB]        
Get:81 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgweather-common all 3.2.0-0ubuntu1 [551 kB]    
Get:82 http://us.archive.ubuntu.com/ubuntu/ oneiric/main liblircclient0 amd64 0.9.0-0ubuntu1 [16.4 kB]     
Get:83 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libopenal1 amd64 1:1.13-2 [233 kB]            
Get:84 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libspeechd2 amd64 0.7.1-6ubuntu1 [18.3 kB]        
Get:85 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libupnp3 amd64 1:1.6.6-5.1 [129 kB]           
Get:86 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libutouch-geis1 amd64 2.1.2-0ubuntu4 [44.3 kB]    
Get:87 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libxcb-keysyms1 amd64 0.3.8-1 [8,068 B]       
Get:88 http://us.archive.ubuntu.com/ubuntu/ oneiric/main mobile-broadband-provider-info all 20110806-1 [37.5 kB]
Get:89 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-brlapi amd64 4.2-8ubuntu5 [86.9 kB]        
Get:90 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-coherence all 0.6.6.2-5ubuntu1 [318 kB]
Get:91 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-louis amd64 2.3.0-2ubuntu1 [5,822 B]       
Get:92 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-oauth2 all 1.5.170-1 [12.4 kB]         
Get:93 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-piston-mini-client all 0.6+bzr48-0ubuntu1 [16.8 kB]
Get:94 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-pycurl amd64 7.19.0-4ubuntu2 [76.0 kB]     
Get:95 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-speechd all 0.7.1-6ubuntu1 [44.2 kB]       
Get:96 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-storm amd64 0.18-1 [130 kB]            
Get:97 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-twisted-conch all 1:11.0.0-1 [270 kB]      
Get:98 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-tz all 2010b-1ubuntu1 [41.1 kB]        
Get:99 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-webob all 1.0.8-1 [273 kB]                 
Get:100 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-wsgi-intercept all 0.4-0ubuntu2 [43.3 kB]
Get:101 http://us.archive.ubuntu.com/ubuntu/ oneiric/main sessioninstaller all 0.20+bzr120-0ubuntu2 [29.0 kB]
Get:102 http://us.archive.ubuntu.com/ubuntu/ oneiric/main speech-dispatcher amd64 0.7.1-6ubuntu1 [471 kB]  
Fetched 15.1 MB in 4min 1s (62.3 kB/s)                                                                     
E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

Please help. Thanks in advance...! :)

---

### Post by 23dornot23d on 2011-10-15
[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

you have plenty of space ?

df

---

### Post by vrraghy on 2011-10-15
yes i do... around 51 GB... large enough, i presume... and i could jus read that page on apt.conf...
but wat exactly am i supposed to do...???

---

### Post by vrraghy on 2011-10-15
Hi,

I updated util-linux via Synaptic and run the command
"*sudo apt-get update && sudo apt-get upgrade*" once again and got this:

```

sudo apt-get update && sudo apt-get upgrade
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                      
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Ign http://us.archive.ubuntu.com oneiric-updates InRelease           
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Hit http://archive.canonical.com oneiric Release.gpg                 
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Ign http://us.archive.ubuntu.com oneiric-security InRelease          
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease          
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg                  
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric-proposed Release.gpg        
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-security Release                      
Hit http://us.archive.ubuntu.com oneiric-proposed Release                      
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources 
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://us.archive.ubuntu.com oneiric-security/main Sources                 
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources 
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources   
Hit http://us.archive.ubuntu.com oneiric-security/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages
Ign http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/main Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://dl.google.com stable InRelease      
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://us.archive.ubuntu.com oneiric-security/main Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-security/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-security/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-security/universe Translation-en
Get:1 http://dl.google.com stable Release.gpg [198 B]
Get:2 http://dl.google.com stable Release [1,347 B]                            
Get:3 http://dl.google.com stable/main amd64 Packages [764 B]                  
Get:4 http://dl.google.com stable/main i386 Packages [779 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Fetched 3,088 B in 1min 15s (41 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot alsa-utils appmenu-gtk apport-gtk apt apt-transport-https
  apt-utils aptdaemon apturl apturl-common at-spi audacity audacity-data
  awn-applet-indicator bamfdaemon banshee banshee-extension-soundmenu
  banshee-extension-ubuntuonemusicstore baobab bind9-host binutils
  bogofilter-bdb brasero brasero-cdrkit brasero-common brltty brltty-x11
  ca-certificates calibre calibre-bin cdrdao checkbox checkbox-gtk cheese
  cheese-common chromium-browser chromium-browser-l10n compiz compiz-core
  compiz-gnome compiz-plugins compiz-plugins-main compizconfig-backend-gconf
  computer-janitor computer-janitor-gtk console-setup cpp cpp-4.5 dnsutils
  doc-base easystroke eclipse-jdt eclipse-pde eclipse-platform
  eclipse-platform-data eclipse-rcp empathy empathy-common eog evince
  evince-common evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-indicator
  evolution-plugins evolution-webcal file-roller filezilla filezilla-common
  firefox firefox-globalmenu flashplugin-installer g++ g++-4.5 gbrainy
  gcalctool gcc gcc-4.5 gcc-4.5-base gcj-4.5-jre-lib gconf-editor gdm gedit
  gedit-common geoclue-ubuntu-geoip gir1.2-appindicator-0.1
  gir1.2-dbusmenu-glib-0.4 gir1.2-freedesktop gir1.2-glib-2.0 glib-networking
  gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center
  gnome-disk-utility gnome-games-common gnome-icon-theme gnome-keyring
  gnome-mahjongg gnome-media gnome-nettool gnome-orca gnome-panel
  gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-user-share gnome-utils-common gnomine gnupg-agent gnupg2 gramps
  grub-common grub-pc gsettings-desktop-schemas gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gtk2-engines-pixbuf
  gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-fuse gwibber
  gwibber-service ia32-libs ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  indicator-application indicator-appmenu indicator-datetime
  indicator-messages indicator-session indicator-sound info iproute
  iputils-ping jockey-common jockey-gtk language-selector-common
  language-selector-gnome lib32asound2 lib32gcc1 lib32ncurses5 lib32ncursesw5
  lib32stdc++6 libalgorithm-diff-xs-perl libapparmor-perl
  libappindicator0.1-cil libappindicator1 libapt-pkg-perl libart2.0-cil
  libasound2 libasound2-plugins libawn1 libbamf0 libbind9-60 libc-bin
  libc-dev-bin libc6 libc6-dev libc6-i386 libcairo-perl libcanberra-pulse
  libcanberra0 libcloog-ppl0 libcompizconfig0 libcurl3 libdecoration0
  libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib
  libdesktop-agnostic-vfs-gio libdesktop-agnostic0 libdigest-sha1-perl
  libdns69 libept1 libequinox-osgi-java libevolution libgail-common libgail18
  libgcc1 libgcj-bc libgcj11 libgconf2.0-cil libgdata1.7-cil libgdu-gtk0
  libgfortran3 libgirepository-1.0-1 libgkeyfile1.0-cil libgl1-mesa-dri
  libgl1-mesa-glx libglade2.0-cil libglib-perl libglib2.0-0 libglib2.0-bin
  libglib2.0-cil libglibmm-2.4-1c2a libgmime2.4-cil libgmpxx4ldbl
  libgnome-bluetooth8 libgnome-keyring0 libgnome-vfs2.0-cil libgnome2.24-cil
  libgnomekbd-common libgomp1 libgtk-sharp-beans-cil libgtk-vnc-1.0-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkmm-2.4-1c2a
  libgucharmap7 libgudev1.0-cil libhighgui2.1 libhtml-parser-perl libindicate5
  libio-pty-perl libisc62 libisccfg62 libisofs6 libjack-jackd2-0 liblapack3gf
  liblaunchpad-integration1.0-cil liblocale-gettext-perl liblucene2-java
  liblwres60 libmagick++3 libmission-control-plugins0 libmlt++3
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-corlib2.0-cil
  libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-system2.0-cil libmono-zeroconf1.0-cil
  libmpc2 libmpfr4 libmusicbrainz4c2a libnautilus-extension1 libncurses5
  libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl
  libnet-dns-perl libnm-glib-vpn1 libnotify0.4-cil libpam-modules
  libpam-modules-bin libpango-perl libphonon4 libplymouth2
  libpulse-mainloop-glib0 libpulse0 libpurple0 libpython2.7 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtgui4 librdf0 libreadline6 libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-writer librsvg2-2
  librsvg2-common libsasl2-2 libsasl2-modules libsigc++-2.0-0c2a libsnmp15
  libstartup-notification0 libstdc++6 libstdc++6-4.5-dev libsub-name-perl
  libsyncdaemon-1.0-1 libtag1-vanilla libtag1c2a libtaglib2.0-cil
  libtelepathy-logger2 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libubuntuone-1.0-1 libubuntuone1.0-cil
  libunity-2d-private0 libuuid-perl libv4l-0 libvte-common libvte9
  libwpd-0.9-9 libwps-0.2-2 libwww-perl libxapian22 libxml-parser-perl
  libzrtpcpp-1.4-0 light-themes lintian linux-generic linux-headers-generic
  linux-image-generic melt menu mono-2.0-gac mono-csharp-shell mono-gac
  mono-gmcs mono-runtime mount mousetweaks nautilus nautilus-data
  nautilus-sendto nautilus-sendto-empathy nautilus-share ncurses-bin
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notify-osd nspluginwrapper ntfs-3g openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openssh-client openssl
  overlay-scrollbar parted perl perl-base perl-modules phonon pidgin
  pidgin-data pidgin-libnotify plymouth plymouth-label protobuf-compiler
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python
  python-appindicator python-apt python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-awn
  python-crypto python-desktop-agnostic python-evolution python-gconf
  python-glade2 python-gnome2 python-gobject python-gtk2 python-ibus
  python-indicate python-minimal python-mlt3 python-openssl python-protobuf
  python-pyatspi python-pythonmagick python-tagpy python-ubuntuone-client
  python-ubuntuone-control-panel python-uno python-vte python-xapian python2.7
  python2.7-minimal rdesktop sat4j seahorse shotwell simple-scan
  software-center software-properties-gtk stellarium supertuxkart
  supertuxkart-data synaptic tcl tcpdump telepathy-idle telepathy-logger
  telepathy-mission-control-5 tomboy totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk twinkle ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk
  unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places
  unity-2d-spread unity-common unity-place-applications unity-place-files
  update-manager update-manager-core update-notifier update-notifier-common
  upower usb-creator-common usb-creator-gtk vim-common vim-tiny vinagre vino
  virtualbox-ose virtualbox-ose-dkms virtualbox-ose-qt vlc vlc-nox
  vlc-plugin-notify vlc-plugin-pulse wget wine wine1.2 wireshark
  wireshark-common wpasupplicant xchat xchat-common xserver-xorg-core
  xserver-xorg-video-intel yelp zenity
0 upgraded, 0 newly installed, 0 to remove and 496 not upgraded.

```

I'm sure I'm still on Natty, and not upgraded.
And on a restart, before and after the login, I got an error message saying something related to libconfig was not configured or something. Not sure.

Meanwhile, I've downloaded the .iso for 11.10. Would that be of any help ?

Thanks in advance...! :)

---

### Post by 23dornot23d on 2011-10-15
ok try 

sudo apt-get installl aptitude

aptitude safe-upgrade

and post the output here before you accept what it gives you ......

---

### Post by vrraghy on 2011-10-15
Did that. The install went fine. And the next command gave just this:
"Segmentation Fault"

On adding "sudo" to that, there was no output.

---

### Post by 23dornot23d on 2011-10-15
Try this ( it does sound like you are still in Natty ...... but you lists are showing the Oneiric repos 

so we will update them and try again ....

sudo apt-get update

---

### Post by vrraghy on 2011-10-15
No, that happened only on the doing this:
"aptitude safe-upgrade"

and i did these 2 steps again. same result. no problem with the update, but Segmentation Fault on upgrade...

---

### Post by 23dornot23d on 2011-10-15
do

sudo apt-get update

and try them again ..... it should not seg fault ......

type

uname -a

and post the result .....
( just want to see what you are running )

The other alternative with it seg faulting is to do a fresh install in a totally clean 20 Gig partition

Then we know everything is ok .....

But you should  have a backup of all you important information 

I usually use a external USB to put a copy of everything I need onto .....

sorry the only other thing is I missed sudo off

try 

sudo aptitude safe-upgrade

if it still seg faults ....

I recommend doing the clean install ...... as above ...... unless someone else can help you 
to get by this problem ..... with the seg fault ...

---

### Post by vrraghy on 2011-10-15
System Monitor tells me that I'm running 11.10.

sudo apt-get update => No errors.

aptitude safe-upgrade => Segmentation Fault

"uname -a" gave out this:

Linux BHISHMA 2.6.38-11-generic #49-Ubuntu SMP Mon Aug 29 20:47:07 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

U was using Windows, and there was a problem with my HD, so I couldn't even boot & thats when I installed Ubuntu. Is this "Segmentation Fault" because of that...???

---

### Post by 23dornot23d on 2011-10-15
It could be a hardware problem you would have to check your logs

in log file viewer

To see what the cause is ...... of the segfault .....

But I notice that although you are running Oneiric ..... we are using the older kernel

Have you tried rebooting recently and going in again ...... maybe it just needs

to be rebooted after all the upgrading and then we can see if the problem still exists.

If not first check your hard drive is ok and then try a fresh install as I said previously

back up any important data if you have not already done so ......

If the Hard Drive is failing for any reason ( The is a smartmon package that can monitor the hard drive )

have you had any hard drive errors show up in the past ...... once they do start to go its best to replace them

If this is the case here ,,,

---

### Post by vrraghy on 2011-10-15
There are many logs in log file viewer. Which one should I post here ?

And yes, I did reboot many a time. But no effect. In fact, am getting another error.
i.e. libconfig is not configured properly. And it takes more time than usual to get into the OS.

And I'm not in a position to replace my HD as of now.

Also, there seem to be some problems with Unity. The buttons on the window borders (Close, min, max) are not showing up unless maximised. CompizConfig, once opened, disappears after a few seconds.

Please suggest some other option for the upgrade. Or at least reset the current 11.04...

Thanks...!!!

---

### Post by 23dornot23d on 2011-10-15
Syslog  and kernel log may help here ......

if you post them put them between code tags as they will be very long ....

or try to find where the segfault information is and just cut and paste that .......

---

### Post by vrraghy on 2011-10-15
I've given below the extracts of the Kernel Log & Syslog

Please help...!

Kernal:

```

Oct 14 11:19:09 BHISHMA kernel: [ 3375.700049] totem-video-thu[3265]: segfault at 7f3364021008 ip 00007f3373859323 sp 00007fff43c41850 error 4 in libc-2.13.so[7f33737e1000+18a000]

Oct 15 14:05:41 BHISHMA kernel: [  681.270394] ccsm[3028] general protection ip:7f98cd8165d1 sp:7fffac5a5b88 error:0 in libc-2.13.so[7f98cd794000+18a000]
Oct 15 14:09:23 BHISHMA kernel: [  903.185691] compiz[2535]: segfault at 38 ip 00007f2aa4709394 sp 00007fffcd123050 error 4 in libpthread-2.13.so[7f2aa4700000+18000]
Oct 15 14:12:38 BHISHMA kernel: imklog 5.8.1, log source = /proc/kmsg started.

Oct 15 14:14:15 BHISHMA kernel: [  110.325193] ccsm[2004] general protection ip:7f5eda72e5d1 sp:7fff6385f2a8 error:0 in libc-2.13.so[7f5eda6ac000+18a000]
Oct 15 14:14:37 BHISHMA kernel: [  132.719200] compiz[1719]: segfault at 38 ip 00007f2d0506f394 sp 00007fff45823170 error 4 in libpthread-2.13.so[7f2d05066000+18000]
Oct 15 14:18:31 BHISHMA kernel: Kernel logging (proc) stopped.
Oct 15 16:28:11 BHISHMA kernel: imklog 5.8.1, log source = /proc/kmsg started.

Oct 15 17:01:22 BHISHMA kernel: [ 2002.179926] aptitude[2770]: segfault at 0 ip 00007f32bae83aaa sp 00007fffb50f7db0 error 4 in libapt-pkg.so.4.11.0[7f32bae06000+115000]
Oct 15 17:01:27 BHISHMA kernel: [ 2007.529922] aptitude[2772]: segfault at 0 ip 00007f4acf56caaa sp 00007fffee3d4150 error 4 in libapt-pkg.so.4.11.0[7f4acf4ef000+115000]
Oct 15 17:01:31 BHISHMA kernel: [ 2011.147078] aptitude[2773]: segfault at 0 ip 00007f686ef15aaa sp 00007fffc20a5650 error 4 in libapt-pkg.so.4.11.0[7f686ee98000+115000]
Oct 15 17:26:43 BHISHMA kernel: [ 3523.637163] aptitude[2885]: segfault at 0 ip 00007f8abfb9daaa sp 00007fffe35095e0 error 4 in libapt-pkg.so.4.11.0[7f8abfb20000+115000]
Oct 15 17:43:35 BHISHMA kernel: [ 4535.797338] aptitude[3060]: segfault at 0 ip 00007fd8e9a23aaa sp 00007fff24de0e00 error 4 in libapt-pkg.so.4.11.0[7fd8e99a6000+115000]
Oct 15 17:43:39 BHISHMA kernel: [ 4540.111620] aptitude[3062]: segfault at 0 ip 00007fca2c1efaaa sp 00007fffb5a68640 error 4 in libapt-pkg.so.4.11.0[7fca2c172000+115000]
Oct 15 17:43:40 BHISHMA kernel: [ 4541.095644] aptitude[3064]: segfault at 0 ip 00007f6f9ae9daaa sp 00007fffea01be80 error 4 in libapt-pkg.so.4.11.0[7f6f9ae20000+115000]
Oct 15 17:43:41 BHISHMA kernel: [ 4541.579897] aptitude[3066]: segfault at 0 ip 00007fc67da4caaa sp 00007fffed5e9040 error 4 in libapt-pkg.so.4.11.0[7fc67d9cf000+115000]
Oct 15 17:43:43 BHISHMA kernel: [ 4543.160061] aptitude[3067]: segfault at 0 ip 00007f2a687bdaaa sp 00007fffbc507340 error 4 in libapt-pkg.so.4.11.0[7f2a68740000+115000]
Oct 15 17:43:43 BHISHMA kernel: [ 4543.868308] aptitude[3068]: segfault at 0 ip 00007f698cb42aaa sp 00007fff23c39810 error 4 in libapt-pkg.so.4.11.0[7f698cac5000+115000]
Oct 15 17:43:44 BHISHMA kernel: [ 4544.817214] aptitude[3069]: segfault at 0 ip 00007f1fd430faaa sp 00007fff19358960 error 4 in libapt-pkg.so.4.11.0[7f1fd4292000+115000]
Oct 15 17:43:44 BHISHMA kernel: [ 4545.097183] aptitude[3070]: segfault at 0 ip 00007f289a2f0aaa sp 00007fffe9e3ae80 error 4 in libapt-pkg.so.4.11.0[7f289a273000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.417155] aptitude[3071]: segfault at 0 ip 00007fa106804aaa sp 00007fffba540480 error 4 in libapt-pkg.so.4.11.0[7fa106787000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.667318] aptitude[3072]: segfault at 0 ip 00007f6c5145daaa sp 00007fff15735960 error 4 in libapt-pkg.so.4.11.0[7f6c513e0000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.907000] aptitude[3073]: segfault at 0 ip 00007f748aafbaaa sp 00007fff230ca160 error 4 in libapt-pkg.so.4.11.0[7f748aa7e000+115000]

```

Syslog:

```

Oct 15 14:09:23 BHISHMA kernel: [  903.185691] compiz[2535]: segfault at 38 ip 00007f2aa4709394 sp 00007fffcd123050 error 4 in libpthread-2.13.so[7f2aa4700000+18000]

Oct 15 14:14:37 BHISHMA kernel: [  132.719200] compiz[1719]: segfault at 38 ip 00007f2d0506f394 sp 00007fff45823170 error 4 in libpthread-2.13.so[7f2d05066000+18000]
Oct 15 14:17:01 BHISHMA CRON[2204]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 14:18:31 BHISHMA kernel: Kernel logging (proc) stopped.
Oct 15 14:18:31 BHISHMA rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="692" x-info="http://www.rsyslog.com"] exiting on signal 15.
Oct 15 16:28:11 BHISHMA kernel: imklog 5.8.1, log source = /proc/kmsg started.
Oct 15 16:28:11 BHISHMA rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="785" x-info="http://www.rsyslog.com"] start
Oct 15 16:28:11 BHISHMA rsyslogd: rsyslogd's groupid changed to 103
Oct 15 16:28:11 BHISHMA rsyslogd: rsyslogd's userid changed to 101
Oct 15 16:28:11 BHISHMA rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 15 16:28:11 BHISHMA kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 15 16:28:11 BHISHMA kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 15 16:28:11 BHISHMA kernel: [    0.000000] Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #49-Ubuntu SMP Mon Aug 29 20:47:07 UTC 2011 (Ubuntu 2.6.38-11.49-generic 2.6.38.8)
Oct 15 16:28:11 BHISHMA kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=bd3301b1-20a7-4695-b99e-18d7a58dbbe7 ro quiet splash vt.handoff=7

Oct 15 17:01:22 BHISHMA kernel: [ 2002.179926] aptitude[2770]: segfault at 0 ip 00007f32bae83aaa sp 00007fffb50f7db0 error 4 in libapt-pkg.so.4.11.0[7f32bae06000+115000]
Oct 15 17:01:27 BHISHMA kernel: [ 2007.529922] aptitude[2772]: segfault at 0 ip 00007f4acf56caaa sp 00007fffee3d4150 error 4 in libapt-pkg.so.4.11.0[7f4acf4ef000+115000]
Oct 15 17:01:31 BHISHMA kernel: [ 2011.147078] aptitude[2773]: segfault at 0 ip 00007f686ef15aaa sp 00007fffc20a5650 error 4 in libapt-pkg.so.4.11.0[7f686ee98000+115000]

Oct 15 17:43:35 BHISHMA kernel: [ 4535.797338] aptitude[3060]: segfault at 0 ip 00007fd8e9a23aaa sp 00007fff24de0e00 error 4 in libapt-pkg.so.4.11.0[7fd8e99a6000+115000]
Oct 15 17:43:39 BHISHMA kernel: [ 4540.111620] aptitude[3062]: segfault at 0 ip 00007fca2c1efaaa sp 00007fffb5a68640 error 4 in libapt-pkg.so.4.11.0[7fca2c172000+115000]
Oct 15 17:43:40 BHISHMA kernel: [ 4541.095644] aptitude[3064]: segfault at 0 ip 00007f6f9ae9daaa sp 00007fffea01be80 error 4 in libapt-pkg.so.4.11.0[7f6f9ae20000+115000]
Oct 15 17:43:41 BHISHMA kernel: [ 4541.579897] aptitude[3066]: segfault at 0 ip 00007fc67da4caaa sp 00007fffed5e9040 error 4 in libapt-pkg.so.4.11.0[7fc67d9cf000+115000]
Oct 15 17:43:43 BHISHMA kernel: [ 4543.160061] aptitude[3067]: segfault at 0 ip 00007f2a687bdaaa sp 00007fffbc507340 error 4 in libapt-pkg.so.4.11.0[7f2a68740000+115000]
Oct 15 17:43:43 BHISHMA kernel: [ 4543.868308] aptitude[3068]: segfault at 0 ip 00007f698cb42aaa sp 00007fff23c39810 error 4 in libapt-pkg.so.4.11.0[7f698cac5000+115000]
Oct 15 17:43:44 BHISHMA kernel: [ 4544.817214] aptitude[3069]: segfault at 0 ip 00007f1fd430faaa sp 00007fff19358960 error 4 in libapt-pkg.so.4.11.0[7f1fd4292000+115000]
Oct 15 17:43:44 BHISHMA kernel: [ 4545.097183] aptitude[3070]: segfault at 0 ip 00007f289a2f0aaa sp 00007fffe9e3ae80 error 4 in libapt-pkg.so.4.11.0[7f289a273000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.417155] aptitude[3071]: segfault at 0 ip 00007fa106804aaa sp 00007fffba540480 error 4 in libapt-pkg.so.4.11.0[7fa106787000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.667318] aptitude[3072]: segfault at 0 ip 00007f6c5145daaa sp 00007fff15735960 error 4 in libapt-pkg.so.4.11.0[7f6c513e0000+115000]
Oct 15 17:43:45 BHISHMA kernel: [ 4545.907000] aptitude[3073]: segfault at 0 ip 00007f748aafbaaa sp 00007fff230ca160 error 4 in libapt-pkg.so.4.11.0[7f748aa7e000+115000]

```

---

### Post by 23dornot23d on 2011-10-15
Compiz appears to be causing the problems .....

although totem shows before it ....  ( nope totem was the day before and probably happened after something else )

You would probably find that by logging into UNITY2D your problems will be resolved
for a working system

Until some more compiz problems get resolved ....

---

### Post by vrraghy on 2011-10-15
Did that. Am on Unity 2D now. And the window borders appear now.

But the icons on the launchbar (the left hand side menubar) are still looking like 11.04.

and Compiz still gets closed in a few seconds once opened.

What am I supposed to do now ?

---

### Post by 23dornot23d on 2011-10-15
What graphics card do you use ?

To solve this problem ..... you could try to re-install compiz

or you can use a desktop environment that does not use compiz

Software Center 

Gnome-shell

or LXDE
XFCE

Use another environment not using the Compiz .......... does UNITY2D use compiz now ?
it shouldn't .....

Hope this helps ..... unless someone else here can sort the compiz problem out for you
I have to go now ..... shopping to do ..... sorry .....

---

### Post by vrraghy on 2011-10-15
The graphics card used is an ATI Radeon. (256 MB, i guess)

Yes, it uses Compiz. And I tried removing it and installing it via Software Center. Not even able to remove. i.e. Nothing happens when I click "Remove".

Trying another desktop environment would be an option, but I'd like to fix this up, since I like certain things in this.

Is there a way to force delete Compiz ???

---

### Post by 23dornot23d on 2011-10-15
(If the system is now to rely on compiz then I doubt it very much that you can remove it ....)


It could be related to your graphics card .... there are a lot of problems being reported with ATI cards ....... 
but that is just a thought ..... check my link in red below ....

In there is a fix for some ATI card problems ..... mainly to do with displaying things properly.

Problem 4 is lock-ups .... but you do not say yours locks up ...... but it does seg fault .....

---

### Post by vrraghy on 2011-10-15
but i just checked... the software center itself seems to be corrupt... unable to install/remove any software...!!!

tell me one thing:
can i burn the 11.10's iso to a cd, boot from it and upgrade directly...? if that would work, would be happier to try it out...!!!

---

### Post by 23dornot23d on 2011-10-15
[https://help.ubuntu.com/community/OneiricUpgrades](https://help.ubuntu.com/community/OneiricUpgrades)

check upgrading using the alternate CD - on that page - near to the bottom in the link provided

---

### Post by vrraghy on 2011-10-15
Tried doing that. Was able to mount the iso, but this command
gksu "sh /media/cdrom/cdromupgrade"

did not do anything at all... what can i do now ?

---

### Post by vrraghy on 2011-10-16
Hi,

I'm unable to boot from a live CD. Also, it's not even showing me the login screen.
I just got into a promt via. Recovery mode. And I cn access my files. I have another Windows machine into which I wanna take  backup, but Samba's not installed. Can't even mount a pen drive into this.

Any solution please ? Thanks in advance.

---

### Post by 23dornot23d on 2011-10-16
With the LiveCd not letting you use the system properly - that is a good indication 
that 11.10 is maybe not suitable for your hardware.

If 11.04 was working ok can you create a new 20 Gig partition and run that unti either

a. The bugs get sorted for the ATI radeon cards.
b. The new LiveCD works after the developers have upgraded it ..... later on.

That will get you a working system again ....... 

Hope that this helps in some way.

[I]I use Nvidia graphics and have never had any real problems ....... my only other advice is 
if its a desktop machine can the graphics card be upgraded in it or changed for a Nvidia ..... just a thought off the top of my head [/I]
( sort of thing I would do if this problem was on my machine )

---

### Post by railen5 on 2012-07-21
I have had this same problem when updating to the newest version. 
I found a fix as follows...
Under update manager go to software sources then the updates tab. 
Next to ..Notify me of a new Ubuntu version:  click drop down to show....for any new version. 
I also made sure that under other software tab the radio button for [http://repository.spotify.com](http://repository.spotify.com) stable non-free....is highlighted
After doing these two actions I now show the upgrade under the update manager that was not there previously.

---

