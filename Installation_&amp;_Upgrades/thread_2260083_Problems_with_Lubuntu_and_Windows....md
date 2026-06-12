---
title: "Problems with Lubuntu and Windows..."
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by gogo3 on 2015-01-09
So, I installed Windows again and simplified the hard disk drives(now Windows is on one big, and not on 2 smaller disks). But, once I installed it, I can't have access to Linux Lubuntu 13.10. How can I get access without getting GRUB again(maybe using the Windows bootloader or booting from a CD)? 

To simply put it, how can I boot it from a CD(ONLY BOOT, NOT TRY OUT(AKA load my Lubuntu files)), put Lubuntu in the Windows bootloader or any other way WITHOUT having to go back to GRUB 2?

---

### Post by nerdtron on 2015-01-09
Boot Linux without GRUB? You love the windows Bootloader that much? (just kidding)

Anyway, any reason to do this? GRUB will let you choose which to boot windows and Linux. I'm not sure of any solution though.

---

### Post by yancek on 2015-01-09
Do you have a Lubuntu or any Linux Live CD to check your partitions.  Since windows can't read a Linux system in a default install, use the Linux CD to see if your Lubuntu was overwritten when you reinstalled windows.  Not much point in trying to boot a system if it isn't there.  Unless you are an experienced windows programmer and familiar with the workings of their boot scripts, the only software I am aware of to boot Linux from windows is EasyBCD which you can download and use on windows.  EasyBCD is basically a GUI front end which modifies the windows boot files and is a dually modified Grub.

---

### Post by Impavidus on 2015-01-09
On reinstalling Windows, it overwrote grub with its own boot loader. You can fix it using a live disk. Boot as "Try Lubuntu". The live disk also allows you to get to your files and copy them to a backup. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Lubuntu 13.10 is end of life. I suggest to install 14.04. Installing this will automatically repair your boot loader.

---

