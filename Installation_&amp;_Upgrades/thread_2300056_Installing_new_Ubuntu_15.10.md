---
title: "Installing new Ubuntu 15.10"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by Fourdan on 2015-10-23
Hi
a) Present status of my portable PC 32/64 bits Intel core2 (bought around 2011)
Dualboot Win7 -** Ubuntu 10.04** Lucid Lynx **now obsolete** - no possible upgrade
Win7 is on C:\  and also some softwares like Corel, Visual Studio VB6, ...
I have a Grub file for dual-boot (Grub 1.9.8 Ubuntu 10)
Ubuntu 10.04 was installed after original Win7
Personal documents are on D:\
Ubuntu is on root F:\

b) I would like to migrate toward Ubuntu 15.10 on F:\
If possible with keeping safely C:\  and  D:\
I have downloaded  <ubuntu-15.10-desktop-i386.iso> on a SD card, ready to burn on a CD
What have I to do ? Is it necessary to format F:\  ? What about my old Grub 1.9.8 ? Delete or not ?
I would appreciate a step by step "guide" from a Ubuntu guru
If I boot from the CD what will be the steps and choices ?
Thanks
Regards
Louis

---

### Post by sudodus on 2015-10-23
Welcome to the Ubuntu Forums :-)

Ubuntu 15.10 is brand new (released right now), but it is supported for only 9 months. There is a long time support version, 14.04 LTS, which corresponds to 10.04 LTS. It is supported until April 2019.

The computer should be able to run all current versions of Ubuntu, also 12.04 LTS and 'community re-spins' based on this old version, which is supported until April 2017. But the amount of RAM makes a difference concerning what to select, so please tell us how much RAM there is in the computer.

-o-

***Backup everything important*** in the computer, because installing an operating system is risky! This includes personal data files and Windows 7 (at the very least, make recovery disks of Windows).

It should work well to select ***'Something else'*** at the installer's partitioning window and select the partition where you have Ubuntu 10.04 now. Format the partition and use it for the root file system '/' with the file system ext4. Swap will be selected automatically. Install the bootloader into the head of the drive (/dev/sda) if the first (or only) internal drive. This means the whole linux system will be new, including the grub bootloader.

---

### Post by kansasnoob on 2015-10-23
Since you're moving from 10.04 I'd also be sure to test various live images first. Ubuntu has migrated to the Unity DE, and GNOME now uses GNOME Shell, Mate forked the old GNOME 2 DE, and there are still Xubuntu, Lubuntu, and Kubuntu:

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Once you figure out which flavor you want to install you might ask which version of that specific flavor would be best to install :D

---

### Post by kansasnoob on 2015-10-23
BTW I frequently recommend using the archived 14.04.1 images because they have the longest kernel support:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

But the earlier images were affected by this horrific bug:

[https://launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

That was particularly problematic because the installer may offer an "upgrade" option, **[COLOR="#FF0000"]but using the upgrade option was known to wipe out Windows!!!!!![/COLOR]**

So be sure to plan ahead ;)

---

