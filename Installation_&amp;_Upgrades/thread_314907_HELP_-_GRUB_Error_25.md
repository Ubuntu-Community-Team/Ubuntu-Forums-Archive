---
title: "HELP - GRUB Error 25"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2006-12-08
I have two IDE plus one USB harddisks with following structure:

 fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100       17021    95763465    f  W95 Ext'd (LBA)
/dev/hda3           17022       24321    58637250   83  Linux
/dev/hda5            5100       10198    40957686    7  HPFS/NTFS
/dev/hda6           10199       16708    52291543+   7  HPFS/NTFS
/dev/hda7           16709       17021     2514141   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10199    81923436    7  HPFS/NTFS
/dev/hdb2           10200       19457    74364885    f  W95 Ext'd (LBA)
/dev/hdb5           10200       19457    74364853+   b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8025    64460781    7  HPFS/NTFS
/dev/sda2   *        8026        9655    13092975   83  Linux
/dev/sda3            9656        9729      594405    5  Extended
/dev/sda5            9656        9729      594373+  82  Linux swap / Solaris


First I had only the two IDE hard disks, with Ubuntu and Windows XP installed. Worked fine !!!

I added the USB hard disk and installed Ubuntu (again 6.10 desktop i386)
When it asked to reboot I got the problems.

It does not matter if I add the USB harddisk or not, the GRUB loader ends with ERROR 25


I booted again from the CD and tried to find the GRUB files, but I don't know where I should look for and what I should do if I find them.

I mounted /dev/hda1   but there is no directory /boot
I tried to mount /dev/hda2  but it does not let me mount it

On the USB drive I do have a /boot/grub directory.


I need to get into my system asap (both Windows and Linux). Please give me hints to fix it.

bye

Ronald

---

### Post by bulldog on 2006-12-08
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

You talk about an USB hard drive,bit I see a Sata.
Did you open your computer by any changes,to connect the new hard disk?
Is it possible you pulled a cable from the connector or something like that?

---

### Post by ELMIT on 2006-12-08
I found in another thread the solution:


I booted from the cd, created a su password and su for the rest below.

1. open in a terminal    grub
2. grub>root (hd ->tab  and complete the line to:
   grup>root (hd0,2)
3. grub>setup (hd0)

reboot and it worked again:
I can boot Ubuntu and XP


I would like now to add the USB drive to GRUB, how do I do that?

Device Boot Start End Blocks Id System
/dev/sda1 1 8025 64460781 7 HPFS/NTFS
/dev/sda2 * 8026 9655 13092975 83 Linux
/dev/sda3 9656 9729 594405 5 Extended
/dev/sda5 9656 9729 594373+ 82 Linux swap / Solaris

BTW, the idea of the entire exercise is to get a portable Linux system with me to run it on any computer. For that I need a bootable hard disk to start Ubuntu. Now I have a running system. If I had already an XP or Linux running, skip this step.

Next is to start VMplayer with a Ubuntu image. This can be started now from XP, Linux or the own Ubuntu version on the USB drive.

I expect with that, to have a travel Linux version with me which should run at any host. Therefore the first part of the disk is left visible to XP and will hold the vm-images and the trucrypt data file.



bye

Ronald Wiplinger

---

