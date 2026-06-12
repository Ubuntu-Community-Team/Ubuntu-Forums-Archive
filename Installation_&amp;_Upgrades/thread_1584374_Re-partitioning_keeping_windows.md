---
title: "Re-partitioning keeping windows"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Ole Andersen on 2010-09-29
Hey all,
I'm currently running ubuntu on my netbook, and vista on my desktop. 
Earlier i had an ubuntu installation alongside my vista, this has resaulted in my desktop making a countdown at booting. After the countdown it boots up vista. 

So i'm aware that there still are som leftovers from my earlier umuntu adventures.... here is my objective:

I want to keep my vista installation intact, BUT i need to clear all earlier grub and ubuntu installations...and finally I want to install a fresh ubuntu 10.04.

How do you guys/girls suggest I approach my objectives?

---

### Post by garvinrick4 on 2010-09-29
> **Ole Andersen said:**
> Hey all,
I'm currently running ubuntu on my netbook, and vista on my desktop. 
Earlier i had an ubuntu installation alongside my vista, this has resaulted in my desktop making a countdown at booting. After the countdown it boots up vista. 

So i'm aware that there still are som leftovers from my earlier umuntu adventures.... here is my objective:

I want to keep my vista installation intact, BUT i need to clear all earlier grub and ubuntu installations...and finally I want to install a fresh ubuntu 10.04.

How do you guys/girls suggest I approach my objectives?Was it a WUBI install?

---

### Post by garvinrick4 on 2010-09-29
If not WUBI run this and post it. In linux install or live Cd
```
sudo fdisk -l
``` (lower case L)

If a WUBI install go to command line of VISTA:
```
bcdedit
```If there is a entry in there that says wubildr then you must remove it.
```
bcdedit delete {indentifier number in here, the one with wubildr}
```

---

### Post by Ole Andersen on 2010-09-29
Hi,
It's not a WUBI install, but at regular installation alongside vista. 
To understand you correct...i need to insert and boot up a live cd og ubuntu (selecting: Run without changes to system) 
And the typing "sudo fdisk -l" in a shell?

I'm not a super user....:)

---

### Post by garvinrick4 on 2010-09-29
yes that will show your partitions, Windows and linux in sda1 sda2 sda3 so on.
sda numbers are the equivalent of C: D: E: and so on in Windows. Windows are formatted in NTFS or Data partitions in NTFS
because linux can read NTFS and so can Windows.

rick@rick-laptop:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       15985   128192511    7  HPFS/NTFS
/dev/sda3           15985       36006   160819192+   5  Extended
/dev/sda4           36007       38913    23350477+   7  HPFS/NTFS
/dev/sda5           21349       22814    11775645   83  Linux
/dev/sda6           15986       17387    11261533+  83  Linux
/dev/sda7           17388       21348    31816701   83  Linux
/dev/sda8           22815       25394    20723818+   7  HPFS/NTFS
/dev/sda9           25395       26707    10546641   83  Linux
/dev/sda10          26708       29385    21511003+  83  Linux
/dev/sda11          29386       30683    10419200   83  Linux
/dev/sda12          30684       31992    10514511   83  Linux
/dev/sda13          31993       36006    32239616   83  Linux

Partition table entries are not in disk order

---

### Post by Ole Andersen on 2010-09-29
Thanks!! I will post the resault tonight.

---

### Post by Ole Andersen on 2010-09-29
Hi again,
please see below partition table.
How should i install ubuntu alongside vista, without damaging vista_

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05a7d608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         392     3147716    7  HPFS/NTFS
/dev/sda2   *       12749       30402   141796352    7  HPFS/NTFS
/dev/sda3             393       12748    99249570    5  Extended
/dev/sda5             393       12240    95169028+  83  Linux
/dev/sda6           12241       12748     4080478+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2010-09-29
If you use manual install and choose sda5 as / (root) and it will automatically use existing swap. This will overwrite your current install and install a new copy of grub and grub boot loader to the MBR. Note that nothing is saved from Ubuntu, but your other partition with Vista will not be touched.

If you have any data in current partition that you want to save, be sure to back it up first. User settings and your files are in /home, system settings will be in files in /etc if you manually customized anything. You also can export a list of installed applications if you want to reinstall all the apps you currently have. If not just reinstall.

---

### Post by Ole Andersen on 2010-09-30
Thanks oldfred,

I took the chance last night and booted the live version of 10.04.
I used gparted and deleted the linux partitions, leaving my vista part unharmed, and ending up with som 149gb of free space. 

Then i just installed 10.04 onto the free space, and i sems both grub and ubuntu is running perfect, alongside vista.

This morning i just powered on my desktop and i think one of my fans are broken - it made a horrible noise as if the bearing was "uneven"....

thank you both for the support.

---

