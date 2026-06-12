---
title: "No active partition"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Tyg on 2006-08-27
I used the live cd to install Ubuntu and deleted the Windows XP partition.  The aim was to move over to Ubuntu and dispense with XP permanently.  

Everything seemed to go OK but, when I try to reboot the message says "No active partition.  Reboot machine."  

I'm also getting this:
The number of cylinders for this disk is set to 2434.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

I have the feeling I've badly screwed this up somewhere, but unfortunately have little idea what I'm doing.  There seems to be threads on partitions, but dealing with dual-booting.  If anyone could help, you could save me going completely nuts!

---

### Post by rutz on 2006-08-27
go to ur bios setup chk if ur hdd is 1st boot device set for booting if not select ur hdd as 1st boot device........ and savr changes and boot ...remove any other cd in ur rom

---

### Post by Tyg on 2006-08-27
Sanity restored!  It worked!  Thank you soooo much! :D

---

