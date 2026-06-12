---
title: "Blackscreen when loading Ubuntu 10.10 setup! (Nvidia Geforce 310m)"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Abhischek on 2010-10-18
Hi all,
I wanted to dualboot-install my Laptop with Ubuntu 10.10 and Windows 7, but when I try to launch the Ubuntu setup, after language selection I get a blackscreen. I know that Ubuntu is loading because I can hear the login sound after a while. But the screen stays black and I can't to anything! Pls. post any solution which could help me, because I really need to use Ubuntu again.

Laptop specs:
Sony Vaio VPCS11V9E
Core i5 M520 2.40 GHZ
Nvidia GeForce 310M
4GB Ram

Tried installing Ubuntu 10.10 64Bit

Thanks,
Abhischek

---

### Post by mabelode on 2010-10-18
i have the same problem with the same graphics card. tried to install 10.10 amd64 from usb and cd. every time when i am booting the image, i see it loading some stuff in console but instead of the setup screen i then get a black screen.

my specs:
HP elitebook 8440p
Core i7 620M 2.66 GHz
Nvidia GeForce 310M
4GB Ram

i just tried it with the 10.10 i386 image. same effect. when i hit f4 and chose run ubuntu from usb i hear the startup sound but still a black screen. could it be because my laptop screen has an 'exotic' max resolution of 1600x900?

i'm going to try older ubuntu versions next.

---

### Post by Abhischek on 2010-10-18
Hmm no I don't think so. My guess is that the Ubuntu setup doesn't properly supports or detects our graphics card. However there are plenty of users who installed Ubuntu with that same graphics card : S 
I hope there is some more input on this error! :(

---

### Post by 1Dagars1 on 2010-10-18
Hi all. I have the same problem on my sony Vaio VPCCW21FX. If you plug in an external monitor you should be able to see everything displayed. Just sucks that you can't use the laptop monitor i know. 

With Ubunti 10.04 after one or two of the first updates the laptop monitor was functioning again. Don't know what got changed but it did work. Only thing was it was with limited graphics...i.e. no 3d acceleration, wobbly windows, etc.

If you install 10.04 and all the updates I would imagine it will work for you. 

I have tried to install 10.10 and i am back to having the monitor on my laptop not working. I tried to update the Nvidia driver (mine is Nvidia GeForce 310m) following the steps outlined on this forum but i received install errors not addressed in the step by step installation instructions so at this point i am assuming that the something has changed from when the instructions were written and Ubuntu 10.10.

I have posted on this forum for additional help but as yet i am waiting for a response.

I have yet to try and add the monitor directly to the display ini file (there are instructions for this somewhere on the forums and i will post an update here when i get the URL) which i am about to try shortly. I am hoping this helps. I am also hoping that whatever Ubuntu/Canonical did in 10.04 gets replicated in their new release soon!

After i try and add the laptop monitor info to the display ini file i will post the results ASAP for you. hopefully it will work for both of us.

If this fails I plan on going back to 10.04 which i know works on my Vaio.

For you, first things first. Try completing the install with an external monitor plugged in.

---

### Post by oldfred on 2010-10-18
I have an older nvidia 9600gt.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mabelode on 2010-10-19
thanks for the hint with the extra monitor.
Luckily I had one at work. after installing I could chose the proprietary nvidia drivers and it worked without the extra monitor.

---

### Post by Abhischek on 2010-10-19
Ok will try it out in a bit. Hope I can find a monitor :S
Also just fyi I think it's a general kernel problem, because I also tried the Fedora 13 setup which didn't work either.

---

### Post by Abhischek on 2010-10-19
Ok I have installed Ubuntu with an external monitor now. But I still can't start Ubuntu although I installed and activated proprietary drivers. When I boot Ubuntu on my Laptopdisplay I get a black/grey screen which lights up 4 times and then stays black/grey for the rest of the time. I can boot to recovery mode though and run failsafe X server. Any suggestions? I really want to use Ubuntu so any help at all would be very much appreciated.

Abhischek

---

### Post by mrnelson1986 on 2010-10-20
> **Abhischek said:**
> Ok I have installed Ubuntu with an external monitor now. But I still can't start Ubuntu although I installed and activated proprietary drivers. When I boot Ubuntu on my Laptopdisplay I get a black/grey screen which lights up 4 times and then stays black/grey for the rest of the time. I can boot to recovery mode though and run failsafe X server. Any suggestions? I really want to use Ubuntu so any help at all would be very much appreciated.

Abhischek

Have you tried adding "nomodeset" to your boot line? Also, for my sony cw series the 260.xx nvidia drivers don't work, but the 256.xx ones do, you have to get them from the archives.  That could be your issue as well (i have a NVIDIA GT 330M graphics card)

---

### Post by Abhischek on 2010-10-20
Hey where should I add the "nomodeset". I've installed the newest drivers now through command line. Ubuntu doesn't even start X server now. It just leaves me with command line login :S So after I installed the drivers, I logged in to my user account and tried this:
```
"sudo startx"
```
Which gave me an output roughly like this: "Kernel Modul doesn't support 260.19..
..
No displays connected- fatal error

I will try to post the exact output from the log file later today. Hope this gives you an idea of my problem.

Thanks for your help

---

### Post by mrnelson1986 on 2010-10-20
> **Abhischek said:**
> Hey where should I add the "nomodeset". I've installed the newest drivers now through command line. Ubuntu doesn't even start X server now. It just leaves me with command line login :S So after I installed the drivers, I logged in to my user account and tried this:
```
"sudo startx"
```
Which gave me an output roughly like this: "Kernel Modul doesn't support 260.19..
..
No displays connected- fatal error

I will try to post the exact output from the log file later today. Hope this gives you an idea of my problem.

Thanks for your help

you add it in the boot line  at the GRUB menu, you know, hit tab or e to modify the boot line, then you add nomodeset to the second to last line (usually has quiet splash in the line) I can't check because I'm at work and using Windoze XP (required) but when I get home I will check

---

### Post by mrnelson1986 on 2010-10-20
home now, you edit during boot at the grub menu by pressing "E" and going to the line that contains "vmlinuz" and adding nomodeset at the end of that line.  To make the change permanent, at the desktop go into the terminal and use "sudo gedit /etc/default/grub" and change it there.  Then save and run sudo update-grub....if you don't do this it won't update the boot line.

---

### Post by bknecht on 2010-10-21
Guys, it happens to them already in the installer.

If you get to the menu you press F6 and choose "nomodeset". This should let you install Ubuntu.

When you reboot after installation you will have to press "e" and edit the line that ends with "splash" and add "nomodeset" at the end. In order for you to not have to do this every time you boot the computer, you should edit /etc/default/grub as root and find again the line with "splash" at the end. Add "nomodeset" just like before, safe the file and run update-grub as root.

This will solve the problem with the black screen. I still can't use 3D graphics with my Sony Vaio though, but at least you have a system that runs.

---

### Post by bortx on 2010-10-21
Same problem here with my sony vaio cw series with NVIDIA GT 330M graphics card.

At least I can work with nomodeset option, but I'll wait for a solution!

Thanks for all!!

---

### Post by luopio on 2010-10-22
This was already an issue with 10.04. I fixed it with a CustomEDID line in xorg.conf (exactly same setup as Abhischek). Unfortunately this does not work with 10.10 anymore. These console commands might help some people:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

They enable the experimental x-server-branch and install newest versions available. Did not work for me though.

[EDIT] the primary monitor does work when you put in "nomodeset" and possibly take away "quiet" and "splash" at the end of the kernel boot options (in grub press e, go to the line where they are, edit, press ctrl+x). BUT this only gives you the VESA-fallback driver (no acceleration, wrong resolution, etc.) [/EDIT]


[EDIT2]*Here's the bug report [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596) [/EDIT2]

---

### Post by pacut on 2010-10-22
Guys,
the issue to me is to have grub menu. I have a fresh and clean install, no other OS on board. I was able to start the LiveCD by setting "nomodeset" under option (F6) and have the installation process completed.

On reboot no way to have something by pressing "e": the system goes ahead and hangs.

Ubuntu 10.10 uses Grub2, correct ? 
So I should edit my grub.cfg, correct ? 
How could I update my grub2 from Live CD into my HDD ?

Any other idea/suggestion ?

Thanks

---

### Post by mrnelson1986 on 2010-10-22
> **pacut said:**
> Guys,
the issue to me is to have grub menu. I have a fresh and clean install, no other OS on board. I was able to start the LiveCD by setting "nomodeset" under option (F6) and have the installation process completed.

On reboot no way to have something by pressing "e": the system goes ahead and hangs.

Ubuntu 10.10 uses Grub2, correct ? 
So I should edit my grub.cfg, correct ? 
How could I update my grub2 from Live CD into my HDD ?

Any other idea/suggestion ?

Thanks

That is tricky...so you have no GRUB menu when you boot? How would you boot into recovery if you didn't have it...if you don't have a GRUB(2) menu then it seems like your install didn't install correctly.

---

### Post by pacut on 2010-10-22
You know what ??? Grub2 requires SHIFT instead of E !!!
I successfully did everything and have my kubuntu working at all !!!

Thanks
Paolo

---

### Post by bknecht on 2010-10-23
Isn't the problem with no dual boot that GRUB just skips over the screen where you can choose? That's also an option you can edit in /etc/default/grub btw. I guess by pressing shift you can get to the GRUB screen though.

I also have a GeForce GT 330M and the thing with the CustomEDIT worked great with 10.04 (and 9.10 btw.) but I don't get my Graphics card running anymore now. Using the vesa driver sucks, I can't work on most programs anymore and I can't even watch movies on the damn thing. I just bought that laptop at the beginning of this year and I can't do pretty basic things with it anymore? This is a serious issue and has to be addressed. What I don't get is that it's obviously a regression, either with the driver or the new version of X. I suspect X because I can't see why nvidia drivers should suddenly all be broken (yes, I tried several), that's why I'll try the recent X branches that were suggested by luopio, but I don't have much faith in it.

If there will ever be a solution it will probably be a new version of X.

---

### Post by Abhischek on 2010-10-23
Hi guys,
So as promised this is the log file from my X server. In my attempt to launch X server, after only being able to boot ubuntu through terminal (tty). 

> [   108.435] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   108.436] X Protocol Version 11, Revision 0
[   108.436] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   108.436] Current Operating System: Linux abhischek-VPCS11V9E 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[   108.436] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=cb0dfdc4-57c4-4d56-ae8e-89d0ba8f9013 ro nouveau.modeset=0 quiet splash nomodeset
[   108.436] Build Date: 16 September 2010  06:18:41PM
[   108.437] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   108.437] Current version of pixman: 0.18.4
[   108.437] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   108.437] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   108.439] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 24 00:33:35 2010
[   108.439] (==) Using config file: "/etc/X11/xorg.conf"
[   108.439] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   108.440] (==) ServerLayout "Layout0"
[   108.440] (**) |-->Screen "Screen0" (0)
[   108.440] (**) |   |-->Monitor "Monitor0"
[   108.440] (**) |   |-->Device "Device0"
[   108.440] (**) |-->Input Device "Keyboard0"
[   108.440] (**) |-->Input Device "Mouse0"
[   108.440] (==) Automatically adding devices
[   108.440] (==) Automatically enabling devices
[   108.440] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   108.440] 	Entry deleted from font path.
[   108.440] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   108.440] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   108.440] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   108.440] (WW) Disabling Keyboard0
[   108.440] (WW) Disabling Mouse0
[   108.440] (II) Loader magic: 0x7d0200
[   108.440] (II) Module ABI versions:
[   108.440] 	X.Org ANSI C Emulation: 0.4
[   108.440] 	X.Org Video Driver: 8.0
[   108.440] 	X.Org XInput driver : 11.0
[   108.440] 	X.Org Server Extension : 4.0
[   108.442] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9069 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[   108.442] (II) Open ACPI successful (/var/run/acpid.socket)
[   108.442] (II) LoadModule: "extmod"
[   108.443] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   108.443] (II) Module extmod: vendor="X.Org Foundation"
[   108.443] 	compiled for 1.9.0, module version = 1.0.0
[   108.443] 	Module class: X.Org Server Extension
[   108.443] 	ABI class: X.Org Server Extension, version 4.0
[   108.443] (II) Loading extension MIT-SCREEN-SAVER
[   108.443] (II) Loading extension XFree86-VidModeExtension
[   108.443] (II) Loading extension XFree86-DGA
[   108.443] (II) Loading extension DPMS
[   108.443] (II) Loading extension XVideo
[   108.443] (II) Loading extension XVideo-MotionCompensation
[   108.443] (II) Loading extension X-Resource
[   108.443] (II) LoadModule: "dbe"
[   108.444] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   108.444] (II) Module dbe: vendor="X.Org Foundation"
[   108.444] 	compiled for 1.9.0, module version = 1.0.0
[   108.444] 	Module class: X.Org Server Extension
[   108.444] 	ABI class: X.Org Server Extension, version 4.0
[   108.444] (II) Loading extension DOUBLE-BUFFER
[   108.444] (II) LoadModule: "glx"
[   108.444] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   108.453] (II) Module glx: vendor="NVIDIA Corporation"
[   108.453] 	compiled for 4.0.2, module version = 1.0.0
[   108.453] 	Module class: X.Org Server Extension
[   108.453] (II) NVIDIA GLX Module  260.19.12  Fri Oct  8 11:41:55 PDT 2010
[   108.453] (II) Loading extension GLX
[   108.453] (II) LoadModule: "record"
[   108.454] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   108.454] (II) Module record: vendor="X.Org Foundation"
[   108.454] 	compiled for 1.9.0, module version = 1.13.0
[   108.454] 	Module class: X.Org Server Extension
[   108.454] 	ABI class: X.Org Server Extension, version 4.0
[   108.454] (II) Loading extension RECORD
[   108.454] (II) LoadModule: "dri"
[   108.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   108.454] (II) Module dri: vendor="X.Org Foundation"
[   108.454] 	compiled for 1.9.0, module version = 1.0.0
[   108.454] 	ABI class: X.Org Server Extension, version 4.0
[   108.454] (II) Loading extension XFree86-DRI
[   108.454] (II) LoadModule: "dri2"
[   108.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   108.454] (II) Module dri2: vendor="X.Org Foundation"
[   108.454] 	compiled for 1.9.0, module version = 1.2.0
[   108.454] 	ABI class: X.Org Server Extension, version 4.0
[   108.454] (II) Loading extension DRI2
[   108.454] (II) LoadModule: "nvidia"
[   108.454] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   108.455] (II) Module nvidia: vendor="NVIDIA Corporation"
[   108.455] 	compiled for 4.0.2, module version = 1.0.0
[   108.455] 	Module class: X.Org Video Driver
[   108.455] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[   108.455] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   108.455] (--) using VT number 8

[   108.475] (II) Loading sub module "fb"
[   108.475] (II) LoadModule: "fb"
[   108.475] (II) Loading /usr/lib/xorg/modules/libfb.so
[   108.475] (II) Module fb: vendor="X.Org Foundation"
[   108.475] 	compiled for 1.9.0, module version = 1.0.0
[   108.475] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   108.475] (II) Loading sub module "wfb"
[   108.475] (II) LoadModule: "wfb"
[   108.475] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   108.475] (II) Module wfb: vendor="X.Org Foundation"
[   108.475] 	compiled for 1.9.0, module version = 1.0.0
[   108.475] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   108.475] (II) Loading sub module "ramdac"
[   108.475] (II) LoadModule: "ramdac"
[   108.475] (II) Module "ramdac" already built-in
[   108.476] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   108.476] (==) NVIDIA(0): RGB weight 888
[   108.476] (==) NVIDIA(0): Default visual is TrueColor
[   108.476] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   108.476] (**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0"
[   108.476] (**) NVIDIA(0): Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
[   108.476] (**) NVIDIA(0): Enabling RENDER acceleration
[   108.476] (**) NVIDIA(0): ConnectedMonitor string: "DFP-0"
[   108.476] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   108.476] (II) NVIDIA(0):     enabled.
[   108.476] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[   108.477] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[   108.477] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[   108.477] (EE) NVIDIA(0):  *** Aborting ***
[   108.477] (II) UnloadModule: "nvidia"
[   108.477] (II) UnloadModule: "wfb"
[   108.477] (II) UnloadModule: "fb"
[   108.477] (EE) Screen(s) found, but none have a usable configuration.
[   108.477] 
Fatal server error:
[   108.477] no screens found
[   108.477] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   108.477] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   108.477] 
[   108.496]  ddxSigGiveUp: Closing log

Hope this helps you in anyway. Because this log is totally cryptic to me :S

Abhischek

---

### Post by fungisamongus on 2010-10-23
> **oldfred said:**
> I have an older nvidia 9600gt.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I've tried all of this here maybe, I just installed it wrong or something. When it tries to ubuntu the screen loads and it is all a scrambled version windows desktop. When I installed ubuntu from the partition screen, I had a hard time trying to figure out root setting, it kept asking me what root configure I wanted to use. the only thing that worked was \ . Any clue what this noob is doing wrong here?

---

### Post by oldfred on 2010-10-23
It looks like your Sony's have a lot of issues with the Nvidia driver.

[http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

Manual install requires you to choose / (root) partition to install to:

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by disappearedng on 2010-10-24
> **oldfred said:**
> It looks like your Sony's have a lot of issues with the Nvidia driver.

[http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

Manual install requires you to choose / (root) partition to install to:

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Can someone try this and confirm if this solves the problem ? 
I don't think it's just a general problem where Nvidia is not working... I think it is specific to the 10.10 distribution which has buggy recommended driver available for Nvidia 310M support.

---

### Post by disappearedng on 2010-10-24
> **disappearedng said:**
> Can someone try this and confirm if this solves the problem ? 
I don't think it's just a general problem where Nvidia is not working... I think it is specific to the 10.10 distribution which has buggy recommended driver available for Nvidia 310M support.

Just tried it. Doesn't work. Blank screen again. 
Nvidia-glx-185, sudo nvidia-xconfig, added the additional 2 option lines under device. STILL NOT WORKING.

---

### Post by Abhischek on 2010-10-24
Hi all,
I've been searching for a solution and I found a site which seems to discuss a similar problem: [HTML]http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup[/HTML]. Please scroll down to the latest post. If you didn't notice Nvidia released a new driver few days ago 260.19.12. Which didn't seem to work for me, but I realized just now that I didn't had updated the kernel yet.So I will try updating the kernel and installing the new driver right away. If that doesn't work I'll try this possible solution:
> Comment by Artem161, Oct 21 (2 days ago)

Drivers from comment by Shibotto ([http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb) [http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb)) works good with final relase of kernel 2.6.36

Link to kernel deb's for ubuntu maverick users: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

Also microphones (internal and external) works good

If anyone wants to go ahead and try said solutions, please post results. As my internet is really slow and it could take a while until I can post mine.

Abhischek

---

### Post by disappearedng on 2010-10-25
check this, someone posted a solution (the last post).
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078) [+&#10084;]

---

### Post by Abhischek on 2010-10-25
Thank you very much disappearedng!!

Finally its working.
Can confirm a working solution to my problem.

---

### Post by disappearedng on 2010-10-25
you are welcome. Just to let you know.

DO NOT UPDATE the nvidia modules (until we all can confirm).

Keep the set of .deb files in your desktop, and if you by mistake updated them, drop to root shell (press SHIFT to boot to recovery mode, then go to that folder and do `dpkg -i *.deb`)

---

### Post by halfjack on 2010-10-26
Hi Abhischek
I have also a Sony vaio Vcps11v9e, i installed ubuntu10.10 64 bit
and i have your same problem. I follow the steps of this link [https://bugs.launchpad.net/ubuntu/+s...rs/+bug/655078(91](https://bugs.launchpad.net/ubuntu/+s...rs/+bug/655078(91) post) but i can't fix my problem.
Can you write step by step what have you done ??
sorry for my english :)

thanks 
halfjack 

P.S.
I had problem with "sudo nvidia-xconfig" ,it say "command not found", and CustomEDID-option .

---

### Post by disappearedng on 2010-10-26
> **halfjack said:**
> Hi Abhischek
I have also a Sony vaio Vcps11v9e, i installed ubuntu10.10 64 bit
and i have your same problem. I follow the steps of this link [https://bugs.launchpad.net/ubuntu/+s...rs/+bug/655078(91](https://bugs.launchpad.net/ubuntu/+s...rs/+bug/655078(91) post) but i can't fix my problem.
Can you write step by step what have you done ??
sorry for my english :)

thanks 
halfjack 

P.S.
I had problem with "sudo nvidia-xconfig" ,it say "command not found", and CustomEDID-option .

You probably haven't installed nvidia-settings. Make sure you have installed all the nvidia binaries mentioned in my post

---

### Post by halfjack on 2010-10-26
i have installed this six files also nvidia-setting_256.53-oubuntu1_amd64.de , controlled twice .

---

### Post by Rho_T on 2010-10-27
Hi Everyone, 

First post so sorry if it rambles. I have Ubuntu 10.10 a new'ish Vaio laptop with an NVIDIA 310m and have had all the same problems - it worked in 10.04 and then didn't when I upgraded to 10.10 - Blank screen and then 'no screens available', etc. I've just fixed it with the following...I've tried to detail things as much as possible. But please bare in mind you will need your laptops custom EDID before starting.

Here we go:

A) Go to the Synaptics Package Manager, do a search for NVIDIA and remove everything. 

B) Download NVIDIA-Linux-x86-256.53.run from the NVIDIA Linux website and save it somewhere

C) Open up a terminal and type ```
/etc/init.d/gdm stop
```D) now type ```
sudo bash
```E) then navigate to the folder where you saved your NVIDIA driver

F) Type```
 ./NVIDIA-Linux-x86-256.53.run
```G) Click yes to everything
 
H) restart and boot up in safe mode (hit shift after bios)
  
I)edit your Xorg .conf file by opening up a terminal and typing ```
sudo gedit /etc/X11/xorg.conf
```J) If you like remove everything in it and paste in the following (you may have to change the customedid path and also your busID) and save:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option  "ConnectedMonitor"  "DFP-0"    
    Option  "CustomEDID"         "DFP-0:/etc/X11/nvidiaedid.bin"
    BusID "PCI:1:0:0"    
EndSection
```K) open the terminal again and type: ```
sudo gedit /etc/default/grub/
```and change the line to the following: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

L) Now often when restarting every is faced with the no screens problem, I think this is due to nouveau being a pain, so open up your terminal again and type ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and in this file at the bottom add the following ```
blacklist nouveau
```I hope that's everything, let me know how you get on.

Rho

---

### Post by mempfiss on 2010-11-03
hi _Rho_T,_

can you help me for change the customedid path and also my busID in xorg.conf file ?
here is hardware info for my notebook.

---

