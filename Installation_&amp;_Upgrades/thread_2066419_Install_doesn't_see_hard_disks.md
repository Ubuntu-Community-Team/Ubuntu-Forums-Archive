---
title: "Install doesn't see hard disks"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by egalua on 2012-10-04
Let me explain. I have a brand new pc (well, a brand new mother board with a used 160Gb sata disk). 
The MB is an Asus P8H 61-M LE  (H61 B3 revision 3.0) (this is what the box says!).
I try to install ubuntu 12.04.1 64 bit from a flash drive.
I stress that the HDD is empty and ubuntu is the only OS which will ever populate it (if I will succeed in the installation).
When booting I have two option for the device: "Flash drive" or "UEFI Flash drive". I tried both with the same result, which follows.
I start ubuntu from the pendrive, then I launch the installation program.
I go through the first step (language selection) and the second step (updates and third part software selection).

The third step should be, in principle, the selection between 
"Clear disk and install" / "Install beside an other OS" / "Manual partitioning"

Instead, it skips directly to manual partitioning (which, anyway, is what I would choose myself). 
At that moment, my disks are
/dev/sda = my 160Gb HDD 
/dev/sdb = my 2Gb usb disk
The problem is that sda is not recognized and the only disk which is shown is sdb, i.e. the usb pendrive. So, the only thing I can do is stopping installation.

On the other side, if I start fdisk inside a shell or GParted, with both of them I can edit sda and I can partition it at my will.

I tried to start the installation tool after having partitioned my HDD or after having cleared all partitions and left it completely empty, but the result is still the same.

I tried to change some options in the bios; in particular, the sata disk can be set to "Ide mode" or "AHCI mode": I tried both of them, but the result is still the same.

I really don't know what else to try... :( :(

TIA for your help.

PS: till tonight I will not be able to do try again, but in any case the output of 
sudo fdisk -l /dev/sda
was absolutely "normal", in the sense that it was exactly like the output I get for my other 3 pc with linux on them, with the obvious differences due to different disk geometry and capacity: that is, something like (when unpartitioned)

[root:~]#  fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067126

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Bucky Ball on 2012-10-04
***Post moved to own thread***

---

### Post by egalua on 2012-10-04
As said in another thread, the problem is solved.

It was due to the fact that the disk was used and it has been used in fakeraid before: the raid metadata where not properly removed.

The fix for the problem was to install in the live distribution dmraid and then remove the metadata with

sudo dmraid -E -r /dev/sda

---

### Post by bentzi259 on 2012-10-04
> **egalua said:**
> As said in another thread, the problem is solved.

It was due to the fact that the disk was used and it has been used in fakeraid before: the raid metadata where not properly removed.

The fix for the problem was to install in the live distribution dmraid and then remove the metadata with

sudo dmraid -E -r /dev/sda

thank you !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
now it works your a king !!!!!!!

---

### Post by egalua on 2012-10-04
Bentzi, it is not me that you have to thank but darkod who, in this post

[http://ubuntuforums.org/showthread.php?p=12277246#post12277246]("http://ubuntuforums.org/showthread.php?p=12277246#post12277246")

in *your* thread, gave the solution.

Anyway, I'm glad you solved: all in all, it was actually the same problem.

---

