---
title: "Hardy... where are my other hard drives?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by linuxted on 2008-04-30
I used to find them in /media/disk after doing a mount...   I don't see them anymore?

I'm nervous as all of my backup stuff is on these disks.

---

### Post by El King on 2008-04-30
Open terminal
Accessories > Terminal
and write
```
sudo fdisk -l
```
it's a small l 
and post back ur results

---

### Post by linuxted on 2008-04-30
> **El King said:**
> Open terminal
Accessories > Terminal
and write
```
sudo fdisk -l
```
it's a small l 
and post back ur results

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0551e1a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0001f968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      238216   120060832+  83  Linux


At least it recognizes it... I think it is /dev/sdb1

---

### Post by linuxted on 2008-04-30
I found it... had to do the following in a perl script:


$path = "/mnt/backup";
$drive = "/dev/sdb1";

# Setup for mounting the directory
print "Making the directory:\n";
print "mkdir $path\n";
system ("mkdir $path");
# Mount the disk.  Older versions were in /media/disk
print "\nMounting the disk:\nmount -t ext3 $drive $path\n";
system ("mount -t ext3 $drive $path");

---

### Post by aimpau on 2008-05-01
Hi. Have the same problem as yours. Can you explain step by step on how did you do it. Thanks.

---

