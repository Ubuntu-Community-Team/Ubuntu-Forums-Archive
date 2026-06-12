---
title: "Cannot start X - Motion Computing m1400"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by cfmackey on 2014-02-02
Hey everyone.
I have a Motion Computing (Gateway) m1400 tablet PC...great little machine...except I've had a hell of a time installing anything on it.

I've settled on installing Xubuntu 12.04.3 32-bit because it's lightweight, and I've had good experience with 12.04 on other machines.

Conventional install methods **failed** (all were on usb-stick):
[LIST]
[*]Xubuntu Desktop CD
[*]Xubuntu Alternate CD
[*]Ubuntu mini.iso
[*]Ubuntu Server CD
[/LIST]
The recurring theme was the installer would get 3/4 of the way through, and then fail. For the non-graphical installers, it was at the "Select and Install Software" part.

I made headway by running the alternate installer again, letting it set up the base system, skipping the "Select and Install Software" portion, and then carrying on at the grub install.

This got me a stable CLI. I generated a sources list (because apt-get kept asking for the install disk), and ran:
```
sudo apt-get install xubuntu-desktop
```
I restarted the system, but it dropped me back into a shell. When I attempted to manually start X it gave me:
```
Fatal server error:
no screens found
```

The output of /var/log/Xorg.0.log is as follows:
```

[    17.811] X.Org X Server 1.12.3
Release Date: 2012-07-09
[    17.811] X Protocol Version 11, Revision 0
[    17.811] Build Operating System: Linux 2.6.24-31-xen i686 Ubuntu
[    17.811] Current Operating System: Linux molly 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686
[    17.811] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=76b02f4d-375f-4e3c-ae76-ea7e90f5d4e5 ro acpi=off splash quiet vt.handoff=7
[    17.811] Build Date: 09 July 2012  05:18:23PM
[    17.811] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support) 
[    17.811] Current version of pixman: 0.30.2
[    17.811]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.811] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.811] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  2 16:19:31 2014
[    17.825] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.826] (==) No Layout section.  Using the first Screen section.
[    17.826] (==) No screen section available. Using defaults.
[    17.826] (**) |-->Screen "Default Screen Section" (0)
[    17.826] (**) |   |-->Monitor "<default monitor>"
[    17.826] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.826] (==) Automatically adding devices
[    17.826] (==) Automatically enabling devices
[    17.837] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.837]     Entry deleted from font path.
[    17.837] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.837]     Entry deleted from font path.
[    17.837] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.837]     Entry deleted from font path.
[    17.842] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.842]     Entry deleted from font path.
[    17.842] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.842]     Entry deleted from font path.
[    17.842] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.842]     Entry deleted from font path.
[    17.842] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    17.842] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.842] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.842] (II) Loader magic: 0x9c55a0
[    17.842] (II) Module ABI versions:
[    17.842]     X.Org ANSI C Emulation: 0.4
[    17.842]     X.Org Video Driver: 12.0
[    17.842]     X.Org XInput driver : 16.0
[    17.842]     X.Org Server Extension : 6.0
[    17.844] (--) PCI:*(0:0:2:0) 8086:3582:14c0:0012 rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
[    17.844] (--) PCI: (0:0:2:1) 8086:3582:14c0:0012 rev 2, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[    17.844] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.844] (II) LoadModule: "extmod"
[    17.886] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.887] (II) Module extmod: vendor="X.Org Foundation"
[    17.887]     compiled for 1.12.3, module version = 1.0.0
[    17.887]     Module class: X.Org Server Extension
[    17.887]     ABI class: X.Org Server Extension, version 6.0
[    17.887] (II) Loading extension MIT-SCREEN-SAVER
[    17.887] (II) Loading extension XFree86-VidModeExtension
[    17.887] (II) Loading extension XFree86-DGA
[    17.887] (II) Loading extension DPMS
[    17.887] (II) Loading extension XVideo
[    17.887] (II) Loading extension XVideo-MotionCompensation
[    17.887] (II) Loading extension X-Resource
[    17.887] (II) LoadModule: "dbe"
[    17.887] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.887] (II) Module dbe: vendor="X.Org Foundation"
[    17.887]     compiled for 1.12.3, module version = 1.0.0
[    17.887]     Module class: X.Org Server Extension
[    17.887]     ABI class: X.Org Server Extension, version 6.0
[    17.887] (II) Loading extension DOUBLE-BUFFER
[    17.887] (II) LoadModule: "glx"
[    17.888] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.908] (II) Module glx: vendor="X.Org Foundation"
[    17.908]     compiled for 1.12.3, module version = 1.0.0
[    17.908]     ABI class: X.Org Server Extension, version 6.0
[    17.908] (==) AIGLX enabled
[    17.908] (II) Loading extension GLX
[    17.908] (II) LoadModule: "record"
[    17.909] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.909] (II) Module record: vendor="X.Org Foundation"
[    17.909]     compiled for 1.12.3, module version = 1.13.0
[    17.909]     Module class: X.Org Server Extension
[    17.909]     ABI class: X.Org Server Extension, version 6.0
[    17.909] (II) Loading extension RECORD
[    17.909] (II) LoadModule: "dri"
[    17.909] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.909] (II) Module dri: vendor="X.Org Foundation"
[    17.909]     compiled for 1.12.3, module version = 1.0.0
[    17.909]     ABI class: X.Org Server Extension, version 6.0
[    17.910] (II) Loading extension XFree86-DRI
[    17.910] (II) LoadModule: "dri2"
[    17.910] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.910] (II) Module dri2: vendor="X.Org Foundation"
[    17.910]     compiled for 1.12.3, module version = 1.2.0
[    17.910]     ABI class: X.Org Server Extension, version 6.0
[    17.910] (II) Loading extension DRI2
[    17.910] (==) Matched intel as autoconfigured driver 0
[    17.910] (==) Matched vesa as autoconfigured driver 1
[    17.910] (==) Matched fbdev as autoconfigured driver 2
[    17.910] (==) Assigned the driver to the xf86ConfigLayout
[    17.910] (II) LoadModule: "intel"
[    17.911] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.938] (II) Module intel: vendor="X.Org Foundation"
[    17.938]     compiled for 1.12.3, module version = 2.99.906
[    17.938]     Module class: X.Org Video Driver
[    17.938]     ABI class: X.Org Video Driver, version 12.0
[    17.938] (II) LoadModule: "vesa"
[    17.939] (WW) Warning, couldn't open module vesa
[    17.939] (II) UnloadModule: "vesa"
[    17.939] (II) Unloading vesa
[    17.939] (EE) Failed to load module "vesa" (module does not exist, 0)
[    17.939] (II) LoadModule: "fbdev"
[    17.940] (WW) Warning, couldn't open module fbdev
[    17.940] (II) UnloadModule: "fbdev"
[    17.940] (II) Unloading fbdev
[    17.940] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    17.940] (==) Matched intel as autoconfigured driver 0
[    17.940] (==) Matched vesa as autoconfigured driver 1
[    17.940] (==) Matched fbdev as autoconfigured driver 2
[    17.940] (==) Assigned the driver to the xf86ConfigLayout
[    17.940] (II) LoadModule: "intel"
[    17.940] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.940] (II) Module intel: vendor="X.Org Foundation"
[    17.940]     compiled for 1.12.3, module version = 2.99.906
[    17.940]     Module class: X.Org Video Driver
[    17.940]     ABI class: X.Org Video Driver, version 12.0
[    17.940] (II) UnloadModule: "intel"
[    17.940] (II) Unloading intel
[    17.940] (II) Failed to load module "intel" (already loaded, 10007310)
[    17.940] (II) LoadModule: "vesa"
[    17.941] (WW) Warning, couldn't open module vesa
[    17.941] (II) UnloadModule: "vesa"
[    17.941] (II) Unloading vesa
[    17.941] (EE) Failed to load module "vesa" (module does not exist, 0)
[    17.941] (II) LoadModule: "fbdev"
[    17.942] (WW) Warning, couldn't open module fbdev
[    17.942] (II) UnloadModule: "fbdev"
[    17.942] (II) Unloading fbdev
[    17.942] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    17.942] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    17.945] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    17.945] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    17.945] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    17.945] (++) using VT number 7


[    17.955] (EE) No devices detected.
[    17.955] 
Fatal server error:
[    17.955] no screens found
[    17.955] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    17.955] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    17.955] 

```

Initial searches suggested I had to install a driver for the onboard intel graphics chip. So I did:
```

sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade

```
...and just to be sure:
```

sudo apt-get install xserver-xorg-video-intel

```

Again I restarted the machine and again it dropped me back into CLI with the same issue.
I've been working on this all day and I'm at a loss.
Anyone have any suggestions?

---

### Post by cfmackey on 2014-02-02
103 views and no suggestions? :(

---

### Post by Bucky Ball on 2014-02-02
startxfce4

Feel free to bump your thread every twenty four hours if you are getting no response. Simply post 'bump'. This still doesn't mean anyone will have anything to add, of course.

---

### Post by cfmackey on 2014-02-02
Thanks, I will. And I'll give that command a try too.

---

### Post by cfmackey on 2014-02-02
```
startxfce4
```
Yields the same results as before.

---

### Post by Bucky Ball on 2014-02-02
Incidentally, sounds like you were almost there on a mini install by what you're saying. You could, at that stage, have simply:
```

sudo apt-get install xfce4 firefox thunderbird gdebi synaptic
```

... and whatever other apps you want and that would have given you a basic system to build up if you want (or not) with a desktop, a browser, email client, and a package manager. xubuntu-desktop is exactly the same as installing Xubuntu, which is I believe what you wanted, but that said, it also drags in apps you may never use. I personally try and avoid that and only ever do minimal installs as a base and add whatever is going to be apporopriate to the machine's purpose in life. ;)

---

### Post by cfmackey on 2014-02-02
I didn't really think about that. But now that you mention it, it makes sense that the xubuntu-desktop metapackage would be the same as installing via desktop disk.

I do want a minimal install, so I'll keep that in mind.

However, are you saying you think this is the reason for my X.org errors?

---

### Post by Bucky Ball on 2014-02-02
Don't know. What happens when you 'startxfce4' at the cursor at boot?

Oh, OK. Just read your post. No different. Hmm.

---

### Post by Bashing-om on 2014-02-02
cfmackey; Hi !

Did xorg get installed ?
```

sysop@1310mini:~$ dpkg -l xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xorg           1:7.7+1ubunt amd64        [color=red]X.Org X Window System[/color]
sysop@1310mini:~$

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cfmackey on 2014-02-03
I installed the Xubuntu desktop metapackage. In turn that installed X.

```
sudo apt-get isntall xubuntu-desktop
```

Also, not to be a jerk, but I don't think I would be getting error messages from X.org, if X.org wasn't installed.

---

### Post by Bashing-om on 2014-02-03
cfmackey; Well,

As no graphics driver will load - vesa, fbdev. or Intel; tends to make me consider that there is a problem with xorg.

What graphics chip do you have ? maybe we can come up with a boot parameter to enable a driver ?
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

[INDENT][INDENT]work'n to find the solution
[/INDENT][/INDENT]

---

### Post by cfmackey on 2014-02-03
So I've already posted a few questions about my motion computing m1400, but I want to be a bit more broad with this post.

I would like to install Ubuntu on my m1400. I am not particular to flavor or desktop environment. But I have been having an unbelievable (well nothings unbelievable with Linux) amount of trouble.

The question is, has anyone done this before, how did they do it, or how would they suggest doing it?

---

### Post by mörgæs on 2014-02-03
Threads merged. 
Please don't create new threads on the same or a closely related topic. Neither this nor bumping makes it more likely that people are going to help.

---

