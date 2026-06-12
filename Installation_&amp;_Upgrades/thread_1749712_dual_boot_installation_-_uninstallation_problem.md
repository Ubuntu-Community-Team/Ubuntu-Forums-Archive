---
title: "dual boot installation - uninstallation problem"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by line3 on 2011-05-04
Hi all, I'm new to the Ubuntu world, but I managed to install Ubuntu 10.10 64 bit along with my Windows 7 OS. 

This is my setup: Windows 7 is on a 500GB harddrive, and I have a 60GB SSD which I installed Ubuntu to (or I think I did, the installation was a bit confusing for me). I remember the "dev loader" was set as the Windows 7 drive.

So today I decided to uninstall Ubuntu because I got tired of having the dual boot option show up every time when I restart. 

I went into Control Panel > Administrative Tools > Computer Management > Disk Management and deleted the partitions that had Ubuntu on it (maybe not the smartest way to do it). 

Now when I restart, I get an error and it says something can't be found, so I get a grub command line. What should I do to get my Windows 7 back? 

Thanks!!
line3

---

### Post by oldfred on 2011-05-04
Grub & windows install a boot loader to the MBR of a drive. That code just jumps to additional code on the drive, so now grub cannot find the additional code to boot. You need to install windows boot loader.

You can use your Windows repairCD to run the fixMBR command.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by line3 on 2011-05-04
That's kind of what I thought, thanks a lot! It works now :)

---

