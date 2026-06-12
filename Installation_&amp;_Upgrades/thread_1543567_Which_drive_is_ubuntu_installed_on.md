---
title: "Which drive is ubuntu installed on?"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by dsub42 on 2010-08-01
Hi Im really new to linux...

I have 2 drives in my pc, each with two partitions on ...

I need to find out which drive / partition ubuntu is installed on.... any ideas how i would do this?

Any help would greatley be appriciated

---

### Post by howefield on 2010-08-01
Try System > Administration > System Monitor and have a look at the File Systems tab.

---

### Post by dsub42 on 2010-08-01
Iv gone there, but how can i tell from that which partition and disk ubuntu is installed on ....?

---

### Post by howefield on 2010-08-01
Post a screenshot of it.

From mine, I can match the Directory to the Device.

---

### Post by dsub42 on 2010-08-01
The problem is that my ubuntu / says that i only have 800mb of space left one it.

However everypartition in my system is only 50% full

It get smore complicated because i have windows on a different disk.

but when i installed ubuntu im lost as to which disk it was installed on ... i need to increase the available space on my ubuntu system

---

### Post by dsub42 on 2010-08-01
[http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-SystemMonitor-1.png](http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-SystemMonitor-1.png)

---

### Post by howefield on 2010-08-01
There you go, sda5 is 97% full.

---

### Post by dsub42 on 2010-08-01
Thats my point ,,,, how can i increase the size? and how do i know which disk sda5 is?

---

### Post by mick222 on 2010-08-01
System-> administration -> disk utility should show all you partitions and drives and what they contain.Use gparted to resize the partition.

---

### Post by dsub42 on 2010-08-01
ingoring the SSD partition ...

There are 2 disks ... samsung and velociraptor ... each has two partitions ... I dont know which disk / partition ubuntu is running off..

---

### Post by dsub42 on 2010-08-01
[http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-500GBHardDiskATASAMSUNGHD501LJ-dev-sdaDiskUtility.png](http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-500GBHardDiskATASAMSUNGHD501LJ-dev-sdaDiskUtility.png)


please look at this screen shot.... does this look like the drive that ubuntu is installed on? ... how can i extend the size of the available space i have??

---

### Post by dsub42 on 2010-08-01
[http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-500GBHardDiskATASAMSUNGHD501LJ-dev-sdaDiskUtility.png](http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-500GBHardDiskATASAMSUNGHD501LJ-dev-sdaDiskUtility.png)

or this...

---

### Post by howefield on 2010-08-01
> **dsub42 said:**
> and how do i know which disk sda5 is?

The one that doesn't have windows on it as you said earlier.

Install GParted using Synaptic Package Manager, this will allow you to resize and manipulate your partitions. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


Probably not wise to do anything until you have backed up your valuable data. Nothing is likely to go wrong, however, it is always risky when manipulating disks when you are new to it, or not for that matter.

---

### Post by TheStroj on 2010-08-01
See the drive that has / written? that's where Ubuntu is installed. Use program GParted to resize the partitions, it's easy, program will show you everything you need for it.

When you're in GParted, select partition that you want to cut of and take some space from it, then add that space to ubuntu partition.

---

### Post by dsub42 on 2010-08-01
does anyone know where i can get a copy of gparted for ubuntu 10.04LTS 64bit?

---

### Post by mick222 on 2010-08-01
use add remove or synaptic to install gparted the ext4 partition is ubuntu

---

### Post by cavalier911 on 2010-08-01
Post the output of ```
blkid
``` and ```
cat /etc/fstab
``` so we can actually see what partitions are mounted by ubuntu
By looking at the pictures I'd say ubuntu is installed in the 80 gig ext4 partition and it's 3.4 gig swap the next one over, they're both in an extended partition. There is no more free space in the extended partition to increase the ext4 partition size. I would decrease the swap partition size to increase the ext4 partition.

---

### Post by dsub42 on 2010-08-01
blkid
=====
matt@matt-desktop:~$ blkid
Command 'blkid' is available in '/sbin/blkid'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative priviledges associated with your user account.
blkid: command not found

========
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=27107a11-2825-4edb-a414-fb4eb963a3fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=80f69b6f-9b71-42c6-b399-f9920cd687f0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
======================

Sorry im really new to ubuntu so I have no idea what either of those commands are?...

I need to extend by about 40gb

Samsungp1 has nothing on it, however it is formatted as ntfs ... how can i extend my ubuntu space using this?

---

### Post by dsub42 on 2010-08-01
"use add remove or synaptic to install gparted the ext4 partition is  ubuntu"

... i have no idea what this means?

---

### Post by dsub42 on 2010-08-01
Can I not just use Gparted and extend the ubuntu partiton using SamsungP1 (which is now empty)?

If so can any one help me as to where I can find a 64bit copy of gparted?

any help would be appriciated

---

### Post by oldfred on 2010-08-01
You can use the Ubuntu liveCD as it includes gparted. You can also download a separate liveCD of gparted only. I have both on my USB to let me boot either easily. There is not a 64 or 32 bit gparted but just gparted ( which I think is 32 bit).

If you install gparted in your install on the hard drive it will let you look at your system but not modify any mounted partitions and never the root as that is the one it is running on.

Since you may not be able to expand / where it is you could move /home or create a separate /data partition and move that data to another partition. All the roots that I have are only 20-25GB as my data is in one common partition.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Oldfred - Converting to data partition
[http://ubuntuforums.org/showthread.php?p=9074762](http://ubuntuforums.org/showthread.php?p=9074762)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

