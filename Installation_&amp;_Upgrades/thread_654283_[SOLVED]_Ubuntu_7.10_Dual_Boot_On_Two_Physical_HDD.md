---
title: "[SOLVED] Ubuntu 7.10 Dual Boot On Two Physical HDDs"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by mjmurf on 2007-12-30
Hi Folks,

I am relatively new to Ubuntu having just installed it on an aging laptop a few days ago.  I am very impressed with it and would like to dual boot my main PC with Ubuntu 7.10 and WinXP (I'm a diehard flight sim fan, otherwise I would ditch Windows completely).  There are two physical HDDs in the box.  My WinXP install is running on a SATA drive and I have a second 40gig IDE drive that I want to run Ubuntu on.  Now, before I attempt the install and possible mess up my Windows install I have a couple of questions....

I would like to install Ubuntu on the 2nd HDD without altering my SATA (WinXP) drive in any way with a boot loader.  I would like the Ubuntu install to be completely independant on the 2nd drive.  I intend to use my BIOS boot menu to select which drive to boot from.  Is this possible with the Ubuntu installer?  Is there anything special I have to do during the install to prevent (GRUB?) from being stalled on my WinXP drive?

Also, I have posted my hardware below.  Can anyone see any potential incompatibilities?

Thanks for your help!!!

Asus P5N32 SLI SE Deluxe mobo
Intel Core2 Duo E6600
2gigs RAM
Nvidia 7950 GT Graphics Card
Soundblaster Xi-Fi

- Murf

---

### Post by confused57 on 2007-12-30
I would recommend that you burn a copy of the Super Grub Disk before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is an excellent boot utility, if you have problems booting Ubuntu or Windows.

Before you boot the live cd to install Ubuntu, you should probably set the drive you're installing Ubuntu on as the first hard drive booted in your bios hd boot order.  During the partitioning step, make a note of how this drive is designated, i.e. /dev/sda, /dev/hda, etc...then when on the last step of the installer, click on the "Advanced" button and replace the default (hd0) with /dev/sda(or however your drive is designated).  This should ensure that your Windows drive's mbr isn't overwritten with grub.  You should be able to boot Windows or Ubuntu from grub, rather than changing bios.

If you're comfortable disconnecting hard drives, you could consider this method:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Added:  You might want to check out Flightgear, which is in the repositories, you may have to enable the universe & multiverse repos...it's an excellent flight simulator.

---

### Post by mjmurf on 2007-12-31
Thanks!  That sounds pretty straight forward. It seems like a bigger problem now is going to be my dual monitor setup. Sounds like there are some problems using different resolutions on each monitor. Oh well, one step at a time. :)

---

