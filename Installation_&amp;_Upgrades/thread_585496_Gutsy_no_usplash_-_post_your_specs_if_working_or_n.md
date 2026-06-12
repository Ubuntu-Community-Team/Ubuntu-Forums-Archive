---
title: "Gutsy no usplash - post your specs if working or not"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2007-10-21
I would like to ask you whether your Gutsy boot-splash and progress bar is working or not.
In any case, please post your system specs, maybe we can determine whats causing the trouble, since there seem to be a lot of people with the same problem.

Heres mine:

Gutsy 64-bit (clean install)
AMD Athlon X2 4400
1G RAM
Nvidia 8500 GT 256 RAM
Samsung SyncMaster 757NF

I have read probably every thread regarding this subjects and tried every possible solution, but in vain. I can`t get usplash to function as it did in Feisty, no matter what I do...

---

### Post by hal8000 on 2007-10-21
Mine is working, but not with the Gutsy 2.6.22 kernel.

My machine would not boot with the gutsy stock kernel, got stuck at waiting for root filesystem.
I believe in this case it is related to the  sata drive emulation and limit of 15 partitions, I have 23 partitions on my hard drive, and I got a similar message with Fedora 7 and Saybon 3.4e linux.

As I have a multiboot system , my solution is easy, I boot into an alternate system and copy one of my other kernels, in this case it is my own self compiled 2.6.21 kernel and its modules, I dont use initramfs or initrd.img and Ubuntu is booting pretty quick, under 25 seconds.

Although this wont solve your problems directly, unless you have another system here is my spec.

Asus P4P800E
Intel P4 2.8G
1G RAM
Sparkle Nvidia 5700Ultra 128M ram

---

### Post by Therion on 2007-10-21
No boot-splash for me (Gutsy 64bit).  I thought maybe, once I had the nVidia drivers installed, I could go back and opt for the splash-screen, but that didn't work out.  I remain "splash-less".

Home build PC:

Asus A8N-SLI
AMD64 4200+ X2  
2GB Corsair
nVidia 8800GTS

---

### Post by tajreed on 2007-10-21
No Gutsy using 2.6.22-14. I must use 2.6.22-12 which fine.

Amd processor, Nvidia 6200

---

### Post by drama1981 on 2007-10-21
at first mine didnt work at all. tried the stock xserver-xorg-ati driver that ships with gutsy. tried the old one from my fiesty install disc. as well as fglrx. no go at all. i get monitor out of range on one monitor and vga not support on the other when it is supposed to show up. must have done sudo dpkg-reconfigure xserver-xorg about 20 times still a no go. so i was looking at various files. i came across the usplash.conf file (its under /etc). i noticed it was set to 1280 1024. but one of my monitors on supports up to 1024x768. so i was like screw it. i did sudo gedit /etc/usplash.conf  and changed it to 1024 768. i now have a partial uspash and progress bar on shutdown. but its not much better than it was before. shreen sits there and flashes at shutdown. almost like its going between a shell and gdm the whole time. now at boot is when it gets really weird i still get the out of range errors at boot (no usplash) but yet it shows during shutdown very weirdly though as described before.


specs:

ubuntu gutsy 7.10 32 bit (stock kernal) (fresh install from alternate cd) (use 32 bit as i have an older intel machine i was gonna run gutsy on too)
amd sempron 3500+ 2.0ghz cpu
512mb ddr
160gb sata
radeon xpress 200 graphics
codename: amberine-m mobo (its an asus board but i dont know the exact model its standard from some compaq desktops)
hp vs17 lcd monitor and mag lt565 lcd monitor (not dual head just tried both seperately)

here is a post i made earlier listing some of the problems ive been having overall (explains the out of range in more detail)

[http://ubuntuforums.org/showthread.php?t=584656](http://ubuntuforums.org/showthread.php?t=584656)

---

### Post by por100pre1 on 2007-10-21
Use startup manager:

```
sudo aptitude install startupmanager
```

or change the resolution manually:

```
sudo cp /etc/usplash.conf /etc/usplash.conf_backup
```

```
gksudo gedit /etc/usplash.conf
```

usplash didn't work fine at first here... :-k

---

### Post by ray bot on 2007-10-21
No usplash here either.

Pentium M 2.13 GHz
1024 MB ram
Nvidia GeForce Go 6600 (nv43) 256 MB
1680 x 1050 LCD panel

---

### Post by avik on 2007-10-21
> **por100pre1 said:**
> Use startup manager:

```
sudo aptitude install startupmanager
```

or change the resolution manually:

```
sudo cp /etc/usplash.conf /etc/usplash.conf_backup
```

```
gksudo gedit /etc/usplash.conf
```

usplash didn't work fine at first here... :-k

Agreed on the last point.  As seen in [this thread]("http://ubuntuforums.org/showthread.php?t=583876"), editing the usplash.conf can fix the issue.

---

### Post by arvinkebob on 2007-10-21
No usplash or x server for that matter.

Gutsy x86 - upgrade
ASUS K8V-X
AMD Athlon 64 2800+
1GB
nVidia 6600GT 128MB AGP
WD HDD 37.4GB partition (80gig drive)

It won't work no matter what kernel I choose at grub and I've removed/reinstalled the nvidia drivers and replaced xorg.conf with a backup but it still won't work. Live CD of 7.10 works fine as well as install. It's just the upgrade that screwed up ubuntu.

---

### Post by aj_watts@optusnet.com.au on 2007-10-21
Install went fine and I got the splash screen and startup progress bar and login panel. All was OK until I added the restricted drivers for the ATI card.

BANG!!!!!!!!!!!!!!!!!!!!!

No the splash works, progress bar gets part of the way through and blank screen and complete system freeze.

SPECS.

Toshiba Satellite P4 1.6G.
512M RAM
ATI Mobility Radean x600 video.

Does anyone have any idea how to get the server back so it is useable with using the ATI drivers (i.e deinstalling the ATI drivers)

---

### Post by heyl1 on 2007-10-27
Hi,

My usplash is not showing at all. Blanc (black) screen. Also, my grub resolution is a bit strange as well, I can't seem to change it either, but at least it's working.

I freshly installed Ubuntu Gutsy a week ago. My usplash wasn't working either then, but I fixed it by changing the usplash.conf to 1024x768.

Today I did a lot of updating and presumably also a new kernel (does anyone know if there is a log file for the updates?). And now, my usplash again won't show and I can't seem to fix it by changing the usplash.conf, the menu.lst or using the startup manager.

Specs:
Latest updates and all Gutsy Gibbon (7.10) i386
Kernel Linux 2.6.22-14-generic

AMD Turion 64 ML-40 (2.2 ghz)
ATI RADEON® XPRESS 200M IGP video
15.4" screen (resolution: 1024x800)

If anyone could help me, thanks very much!

---

### Post by YMas on 2007-10-28
No bootsplash screen - not a major issue.

The screen is off until the login prompt screen (xorg.conf settings), I do see the 'kernel alive' message.

[img]http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=48117&d=1193571831[/img]

--Edit-- 
**Problem solved using [_link_]("https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56") provided by hlmuller.**
I only used vesafb - Many thanks for your help.

Regards,
YMas

---

### Post by hlmuller on 2007-10-28
orange2k identified this solution in bug [150930.]("https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56")

I left out vga16fb, as I didn't need it.  It worked for a fresh Gutsy install on a Dell Inspiron 1420. (Intel T7500 2.2GHz/800FSB / Nvidia 8400M GS 128MB / 1440x900)

---

### Post by Culito on 2007-10-31
Is there different settings for the shutdown and bootup splashes?
I finally got my boot up splash working (using startup manager) but when I shutdown, I just get a blank screen with a cursor in the upper left corner.

Ideas?

---

### Post by lonesomecrow on 2007-11-02
> **YMas said:**
> No bootsplash screen - not a major issue.

The screen is off until the login prompt screen (xorg.conf settings), I do see the 'kernel alive' message.

[img]http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=48117&d=1193571831[/img]

--Edit-- 
**Problem solved using [_link_]("https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56") provided by hlmuller.**
I only used vesafb - Many thanks for your help.

Regards,
YMas

hey man gracias a lot for the link,,,.....

---

### Post by tech0007 on 2007-11-02
Usplash didn't work on fresh gutsy install.  Found this tip and it worked!

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by stevie_velvet on 2007-11-02
> **YMas said:**
> No bootsplash screen - not a major issue.

The screen is off until the login prompt screen (xorg.conf settings), I do see the 'kernel alive' message.

[img]http://ohioloco.ubuntuforums.org/attachment.php?attachmentid=48117&d=1193571831[/img]

--Edit-- 
**Problem solved using [_link_]("https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930/comments/56") provided by hlmuller.**
I only used vesafb - Many thanks for your help.

Regards,
YMas

well rescued using VESA via the alternate cd
The use the nvidia driver in Restricted Drivers Manager within Gnome (administration)

---

### Post by locutus42 on 2008-02-10
Kubuntu 7.10 on Compaq R4000 w/ATI Mobility 200M  latest/greatest updates.
Worked after initial installation and, IIRC after system updates
Stopped working after fglrx restricted driver installation
Worked after enabling the VesaFB module in init ramdisk as mentioned a couple of entries up. I only enabled Vesafb since I figure there's probably not many graphics cards which don't support that standard.

```

sudo vi /etc/initramfs-tools/modules
[add] vesafb

sudo vi /etc/modprobe.d/blacklist-framebuffer
[comment out(add #)] vesafg

sudo update-initramfs -u

```

---

