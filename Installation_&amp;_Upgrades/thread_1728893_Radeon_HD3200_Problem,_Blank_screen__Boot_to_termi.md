---
title: "Radeon HD3200 Problem, Blank screen / Boot to terminal"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by Jelee8804 on 2011-04-14
Hi all,

I've been trying to dual-boot Ubuntu 10.10 with Vista for quite some  time now, but I've been stuck on a certain issue. I did extensive  research on Ubuntu Forums, Ubuntu Help, and Google searches, and I found  out that a lot of people are experiencing the same problem, but none of  the solutions worked for me. I thought maybe you could give me some  insight on the matter.

When I first tried booting from a LiveUSB, my monitor went blank and  told me there was no input signal. I found out that my HDMI connection  was the problem, so I connected my older monitor via analog DVI cable  and I was able to install Ubuntu.

I didn't want to keep using the old monitor, so I installed the  Proprietary Drivers from System>Administration>Additional Drivers,  but when I rebooted to complete the update, the system booted straight  to the Terminal (TTY1). I am unable to enter the GUI, and the command  startx failes, telling me to look at a Xorg.0.log file.

If I choose recovery mode, and choose failsafe mode with reduced  graphics, I am able to boot with GUI on my old monitor. I tried  completely uninstalling the drivers, and manually installing my  appropriate drivers from the ATI website, but I run into the same  problem.

Lastly, some people suggested that I push 'e' from my GRUB2 menu and add  "nomodeset" without quotes before, after, or instead of "quiet splash"  on the edit menu that appears. I tried all three, and none of them  seemed to work. 

I'm really at a loss and don't know how to proceed from here. I was able  to install Ubuntu perfectly fine on my friend's computer (who uses an  nVidia GPU). I was able to download the recommended drivers for her, and  everything was a breeze. 

In case it's helpful, here is my computer setup:
-Gateway LX6200-01
-AMD Phenom X4 64bit processor
-750GB HDD
-8GB DDR2 RAM
-ATI Radeon HD 3200 Integrated Graphics Card

Do you have any suggestions for me?

Lastly, here are the contents of my Xorg.0.log file:
```
[   699.108] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   699.109] X Protocol Version 11, Revision 0
[   699.109] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[   699.109] Current Operating System: Linux Jupo-Ubuntu 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686
[   699.109] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-28-generic-pae root=UUID=546f1a9f-bc00-4cbb-8226-7d1b190813dd ro nomodeset
[   699.109] Build Date: 09 January 2011  12:14:58PM
[   699.109] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   699.109] Current version of pixman: 0.18.4
[   699.110]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   699.110] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   699.111] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 14 16:55:25 2011
[   699.111] (==) Using config file: "/etc/X11/xorg.conf"
[   699.111] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   699.112] (==) No Layout section.  Using the first Screen section.
[   699.112] (==) No screen section available. Using defaults.
[   699.112] (**) |-->Screen "Default Screen Section" (0)
[   699.112] (**) |   |-->Monitor "<default monitor>"
[   699.112] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   699.112] (**) |   |-->Device "ATI radeon HD 3200"
[   699.112] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   699.112] (==) Automatically adding devices
[   699.112] (==) Automatically enabling devices
[   699.113] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   699.113]     Entry deleted from font path.
[   699.113] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   699.113] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   699.113] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   699.113] (II) Loader magic: 0x81f9b00
[   699.113] (II) Module ABI versions:
[   699.113]     X.Org ANSI C Emulation: 0.4
[   699.113]     X.Org Video Driver: 8.0
[   699.113]     X.Org XInput driver : 11.0
[   699.113]     X.Org Server Extension : 4.0
[   699.114] (--) PCI:*(0:1:5:0) 1002:9610:1025:0190 rev 0, Mem @ 0xd0000000/268435456, 0xfe5f0000/65536, 0xfe400000/1048576, I/O @ 0x0000c000/256
[   699.114] (--) PCI: (0:2:0:0) 14f1:8880:1461:d439 rev 15, Mem @ 0xfe600000/2097152
[   699.115] (II) Open ACPI successful (/var/run/acpid.socket)
[   699.115] (II) LoadModule: "extmod"
[   699.115] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   699.115] (II) Module extmod: vendor="X.Org Foundation"
[   699.115]     compiled for 1.9.0, module version = 1.0.0
[   699.116]     Module class: X.Org Server Extension
[   699.116]     ABI class: X.Org Server Extension, version 4.0
[   699.116] (II) Loading extension MIT-SCREEN-SAVER
[   699.116] (II) Loading extension XFree86-VidModeExtension
[   699.116] (II) Loading extension XFree86-DGA
[   699.116] (II) Loading extension DPMS
[   699.116] (II) Loading extension XVideo
[   699.116] (II) Loading extension XVideo-MotionCompensation
[   699.116] (II) Loading extension X-Resource
[   699.116] (II) LoadModule: "dbe"
[   699.116] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   699.116] (II) Module dbe: vendor="X.Org Foundation"
[   699.116]     compiled for 1.9.0, module version = 1.0.0
[   699.116]     Module class: X.Org Server Extension
[   699.116]     ABI class: X.Org Server Extension, version 4.0
[   699.116] (II) Loading extension DOUBLE-BUFFER
[   699.116] (II) LoadModule: "glx"
[   699.117] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   699.117] (II) Module glx: vendor="X.Org Foundation"
[   699.117]     compiled for 1.9.0, module version = 1.0.0
[   699.117]     ABI class: X.Org Server Extension, version 4.0
[   699.117] (==) AIGLX enabled
[   699.117] (II) Loading extension GLX
[   699.117] (II) LoadModule: "record"
[   699.117] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   699.117] (II) Module record: vendor="X.Org Foundation"
[   699.117]     compiled for 1.9.0, module version = 1.13.0
[   699.117]     Module class: X.Org Server Extension
[   699.117]     ABI class: X.Org Server Extension, version 4.0
[   699.117] (II) Loading extension RECORD
[   699.117] (II) LoadModule: "dri"
[   699.118] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   699.118] (II) Module dri: vendor="X.Org Foundation"
[   699.118]     compiled for 1.9.0, module version = 1.0.0
[   699.118]     ABI class: X.Org Server Extension, version 4.0
[   699.118] (II) Loading extension XFree86-DRI
[   699.118] (II) LoadModule: "dri2"
[   699.118] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   699.119] (II) Module dri2: vendor="X.Org Foundation"
[   699.119]     compiled for 1.9.0, module version = 1.2.0
[   699.119]     ABI class: X.Org Server Extension, version 4.0
[   699.119] (II) Loading extension DRI2
[   699.119] (II) LoadModule: "fglrx"
[   699.120] (WW) Warning, couldn't open module fglrx
[   699.120] (II) UnloadModule: "fglrx"
[   699.120] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   699.120] (EE) No drivers available.
[   699.120] 
Fatal server error:
[   699.120] no screens found
[   699.120] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   699.121] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   699.121]
```

---

### Post by zvacet on 2011-04-14
In  System>Administration>Additional Drivers see if driver is installed and is it **in use**.I had problem with that driver,because it was installed,but not in use.I uninstalled **xserver-xorg-video-radeon** and then reinstall **fglrx **from System>Administration>Additional Drivers.Typed 

```
glxgears
```

and see gears working and moving.But I never used HDMI.

---

### Post by Jelee8804 on 2011-04-14
Hi zvacet,

Yes, I confirmed in recovery failsafe mode that the driver is in use. When I go to system > administration > additional drivers, it says that the driver is active.

what do you mean by glxgears?

---

### Post by zvacet on 2011-04-14
Run that command in terminal

```
glxgears
```

you should see gears working.

---

