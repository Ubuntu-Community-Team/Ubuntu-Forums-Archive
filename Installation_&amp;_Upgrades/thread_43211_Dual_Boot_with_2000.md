---
title: "Dual Boot with 2000"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by Nixforce on 2005-06-21
Hi there,

I am planning on changing my OS from 2000 Server to Ubuntu.. Is there a way to break a win2000 server partition while installing Ubuntu? as would like to dual boot initially.

---

### Post by defkewl on 2005-06-21
Create a ext3/reiserfs and swap partition first to install Ubuntu. You can do this visually with Partition magic from windows.

---

### Post by mingus on 2005-06-21
[QUOTE=Nixforce]Hi there,

I am planning on changing my OS from 2000 Server to Ubuntu.. Is there a way to break a win2000 server partition while installing Ubuntu? as would like to dual boot initially.[/QUOTE]

The short answer is, yes that is possibile - but it shouldn't happen with a careful plan:

The primary risk is with the partition table.  If it gets corrupted, and Windows /fixboot cannot repair it, you may have to reformat.

A secondary and lesser risk is with installation and/or configuration of the boot loader.  Be sure to have a W2K install CD or a W98/ME/DOS bootable diskette to repair the MBR if necessary.

Backup everthing and make sure you can do a recovery.

Plan the partitions in advance (search the Wiki).  The most common is either 3 (/, /home, swap) or 4 (/, /boot, /home, swap).  If on the same disk as Windows, safest to place /boot on a logical.  

Partitioning the Windows disk is the greatest risk.  Mixing partitioning tools, or using a tool not native to the OS using those partitions, is the most common source of corrupting the table.   So . . .

Using a separate disk for Linux is safest, no partition conflicts possible.

If partitions were created by the Windows installer or Disk Manager, try not to change them.  If you must, using Partition Magic is the safest.  Do not use Disk Manager or DOS fdisk!

If PM was needed above, then use PM to create the linux partitions, too.  Don't format them with PM; use the Ubuntu installer to do that.

If PM is not needed for the Windows partitions, then use the Ubuntu installer in expert mode to create the linux partitions. 

If a Windows partition must be resized down, defrag and run chkdsk /r beforehand.

For the boot loader, there are a number of alternatives.  Ubuntu's default is to automatically setup the dual-boot and install GRUB to the MBR.  However, this does not always work right.  GRUB can later be installed on any partition or bootable device (like a floppy).  LILO is available as an alternative, and can be put to the MBR, any partition, or another device.

Hope this is a useful start.

---

### Post by Nixforce on 2005-08-23
Hi there,

Me again.. I have a 120 Gig Second HDD in.. XP is on the 70 Gig First Drive.. When i boot off the CD, will it allow me to install on the second HDD and then give the option of Dual boot... The second drive has 5 partitions on, and would like to keep it broken as will install other Distros from time to time, and will also use one of the partitions as a backup of my primary.

---

### Post by mingus on 2005-08-23
[QUOTE=Nixforce]Hi there,

Me again.. I have a 120 Gig Second HDD in.. XP is on the 70 Gig First Drive.. When i boot off the CD, will it allow me to install on the second HDD and then give the option of Dual boot... The second drive has 5 partitions on, and would like to keep it broken as will install other Distros from time to time, and will also use one of the partitions as a backup of my primary.[/QUOTE]

I haven't done this exactly with the Ubuntu installer, but I believe this is no problem.  You probably will want to use the "expert" install option, which gives you more control.  When you come to the partitioning step (and given your desire to install multiple distros), be sure to select an hdb partition with / as the mount point.

The dual-booting part can be a bit tricky, depending on how your BIOS handles boot devices and how you've configured the boot sequence.  The default is to install GRUB in the Master Boot Record, and use it to control the boot.  However, I would suggest installing GRUB to a boot floppy first, and not the hard drive because you may need to tweak GRUB's menu file.  You can test with the floppy and when you're sure everything is OK, then install GRUB to the MBR.

---

### Post by Vitor P. on 2005-08-23
Hello all,

 I also tried to install Ubuntu in dual boot mode with W2K, but I had some problems. I have W2K installed in one HD (IDE0, master) and I tried to install ubuntu in another HD (IDE0, slave).

 First, I was unable to install ubuntu when the disk was formatted with the FAT32 file system. I got an error at about 20% of the installation of the base system. When I changed the file system to ext3 it worked.

 My plan was to use the windows boot loader to control the dual boot process. But I couldn´t find an option to create an ubuntu boot disk at the end of the installation process, which would be necessary to add the ubuntu in the list of the bootable systems.

 Finally, when I tried to start the W2K after the installation, it got stucked because it couldn´t recognize the file system in the second disk (because it was formatted with ext3).

 So, my questions are:

1. How to create a boot disk at the end of the installation process of ububtu?

2. Is it possible to "tell" windows not to read the second disk formatted with ext3?



[QUOTE=Nixforce]Hi there,

I am planning on changing my OS from 2000 Server to Ubuntu.. Is there a way to break a win2000 server partition while installing Ubuntu? as would like to dual boot initially.[/QUOTE]

---

### Post by mingus on 2005-08-23
You definitely do not want to install the Linux root on FAT32, because this filesystem is not journaled.

Not sure what you are referring to by "creating an ubuntu boot disk . . . to add ubuntu in the list of bootable systems."  The Windows loader (ntldr) cannot directly boot another OS.  What you need to do is to create an Ubuntu boot sector and then copy that as a file to Windows c:\, and then add a menu line for that file in boot.ini.  This is called "chain-loading."

There are numerous articles on the web on how to do this, with several different variations.  Here is one that should work:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

---

