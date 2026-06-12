---
title: "Edited WinXP startup OS list, no boot"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Brachabre on 2009-04-04
I have WinXP and Wubi 9.04 installed on one harddrive. I do not have GRUB installed, I use the WinXP boot loader instead. 

In Windows, I manually edited the WinXP OS startup list by swapping the WinXP and Ubuntu lines such that Ubuntu will always be on top (hence if the timer runs out, Ubuntu will always be the default OS of choice). Now, I cannot boot any partitions. I have tried using recovery boot disks with no avail. I have tried fixmbr, ntfsfix, and used Supergrub boot disk to try to atleast boot my windows partition up so I can go back and fix my mistake. 

Here's my fdisk output:

Disk: /dev/hda 120GB

Partitions:  /dev/hda1 * HPFS/NTFS <-------- WinXP and Ubuntu 9.04 (wubi install)
                /dev/hda2    W95 Ext'd (LBA)
                /dev/hda5    HPFS/NTFS
                /dev/hda6    HPFS/NTFS

Hda5/6 have NO UBUNTU on them, they are WinXP personal file partitions.

I have the tools at my disposal, any suggestions are much appreciated, Thanks!):P

---

### Post by phenest on 2009-04-04
Is this a dual boot system? If so, boot a Live CD, and amend the boot.ini from Ubuntu. If it's not dual boot, you're gonna need to install grub.

---

