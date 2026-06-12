---
title: "Grub Error 21"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by jusmurph on 2007-05-10
To begin with it is worth noting i am completely new at linux, relatively experienced windows user wanting to give Linux a try. I cleared and made a partition on a storage drive (ready for the install) so i can dual boot.

I downloaded the live cd for amd64 Ubuntu 7.04 played, liked it so i went to install. After much forum searching i sort of worked out how to get on my desired partition... i think?

It is on a partition of a computer with 4 hard drives... [**Image**]("http://img10.imagepile.net/img10/4470install.jpg")

So the install  progress bar whirls around and then it goes to launch Grub 1.5 and errors with Error 21.

I have tried to search the forums and it nothing seemed to fit my niche.

Any help would greatly be appreciated.

(Also, while the desired option would be to get Ubuntu working and have a dual boot system, i wouldn't mind someone pointing me to how to be able to just go back to windows.)

Thanks all.

---

### Post by confused57 on 2007-05-10
You can boot the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

The one time I experience grub error 21, I had to go into bios and change the hard drive controller from "off" to "auto".

If you need to your Windows booting again:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

from the above link, if you have a Window's XP install cd(not a recovery cd), you can boot up the XP install cd, enter "r", then the command FIXMBR, which should restore Window's IPL code to the mbr...see the link above.

If you don't have a Window's install cd and have access to another computer, you can download a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can boot Windows or Ubuntu and restore either IPL code to the mbr.

---

### Post by jusmurph on 2007-05-10
Thanks for the post.

I found this [thread]("http://ubuntuforums.org/showthread.php?t=438563&highlight=grub+error+21") (Which was posted between searching the forums last night for me and posting this morning).

Which states it can't find the disk. Some more information:
It is a sata (sata1) disk. Nothing has changed in the physical structure of the computer. 

I will try the following and post my results when i get home from work:

Check my bios as stated above

run fdisk -l (small L) 

cat /boot/grub/menu.lst

sudo fdisk -l

---

### Post by psusi on 2007-05-10
You mean the install finished, and when it reboots, you get grub error 21?

This is caused by having a mix of ide and scsi or sata disks.  Grub assumes that your computer boots from the first ide disk if you have one.  You will need to reinstall grub, telling it that your computer in fact, boots from the first sata disk, which I am guessing it is doing as that appears to be where you have windows installed.  I am assuming that sda1 is your windows boot partition, and that you want grub to be able to boot that, as well as your ubuntu install on sdb4. 

Boot from the livecd, open a terminal and enter the following:

sudo grub
device (hd0) /dev/sda
device (hd1) /dev/sdb
root (hd1,3)
setup (hd0)
exit

---

### Post by jusmurph on 2007-05-10
> **psusi said:**
> You mean the install finished, and when it reboots, you get grub error 21?

This is caused by having a mix of ide and scsi or sata disks.  Grub assumes that your computer boots from the first ide disk if you have one.  You will need to reinstall grub, telling it that your computer in fact, boots from the first sata disk, which I am guessing it is doing as that appears to be where you have windows installed.  I am assuming that sda1 is your windows boot partition, and that you want grub to be able to boot that, as well as your ubuntu install on sdb4. 

Boot from the livecd, open a terminal and enter the following:

sudo grub
device (hd0) /dev/sda
device (hd1) /dev/sdb
root (hd1,3)
setup (hd0)
exit

Wow that sucks...

I have no idea about which hard drive is which anymore.

I'm pretty sure, off memory here at work, that windows runs off the ide, what sata drive this partition is on i would have no idea.

Assuming that it was not the first of 3 sata drives... would there be any faults caused (to windows and linux) by changing it, (unpluging it and pluging it into the first sata) to the first one given that the sata drives are all sata storage drives? Or is this just a grub thing where i need to map it to the right drive?

---

### Post by jusmurph on 2007-05-11
Maybe this is an idea...

Restore Windows back to working order

I transfer the data from the IDE (data partition) to the partion im using as linux. Then install Linux next to Windows on the ide... will this solve this problem?

---

### Post by psusi on 2007-05-11
Reinstalling grub is the way to solve the problem, so I just need to know how you are planning on using each of the drives.  You have a lot of drives with a lot of ntfs partitions.  What are they used for?  You seem to have an IDE drive connected to the second ide controller in the system ( shows as hdc ) with two ntfs partitions, and 3 sata disks, two of which have two ntfs partitions, and one has one.  

So you have a total of 7 ntfs partitions.  What are they all used for?  Which is the one that holds windows?

---

### Post by jusmurph on 2007-05-11
> **psusi said:**
> Reinstalling grub is the way to solve the problem, so I just need to know how you are planning on using each of the drives.  You have a lot of drives with a lot of ntfs partitions.  What are they used for?  You seem to have an IDE drive connected to the second ide controller in the system ( shows as hdc ) with two ntfs partitions, and 3 sata disks, two of which have two ntfs partitions, and one has one.  

So you have a total of 7 ntfs partitions.  What are they all used for?  Which is the one that holds windows?

It is the very first partition. All of the NTFS Partitions are all windows storage files etc...

HDC1

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16709   134215011    7  HPFS/NTFS
/dev/sda2           16710       24321    61143390    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2   *       10200       24321   113434965    7  HPFS/NTFS
/dev/sdb3            3825        4120     2377620   82  Linux swap / Solaris
/dev/sdb4            4121       10199    48829567+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551       14593    96735397+   7  HPFS/NTFS

Disk /dev/sdd: 4110 MB, 4110416896 bytes
33 heads, 63 sectors/track, 3861 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3862     4014063    6  FAT16

```

---

### Post by psusi on 2007-05-12
Ok, then in that case, change my original instructions to this:

sudo grub
device (hd0) /dev/hdc
device (hd2) /dev/sdb
root (hd2,3)
setup (hd0)
exit

Also if you could post your /boot/grub/menu.lst file as that will probably need some adjustments as well.

---

### Post by Echo5ive on 2007-05-15
Thanks for this thread -- ran into the exact problem myself, with one SATA disk and two IDE disks.

I *think* I got around the biggest hurdle, but now I get an error 17 from grub instead, which is apparently "unknown file system". I'll be back with some details and an "fdisk -l" in a bit.

---

### Post by Echo5ive on 2007-05-15
Yay, more trouble. I discovered that my disks appear as SCSI devices -- and the order changes depending on if I have my iPod connected at boot or not. The 320 gig disk is a SATA, the other two are IDE disks.

Without iPod:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       14596    91642792+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2442    19615333+  83  Linux
/dev/sdb2            2551       15017   100141177+   7  HPFS/NTFS
/dev/sdb3            2443        2550      867510    5  Extended
/dev/sdb5            2443        2550      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+   6  FAT16
/dev/sdc2            2551       38913   292085797+   7  HPFS/NTFS

```

With iPod: (the iPod is /dev/sda, cut it from the output.)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   6  FAT16
/dev/sdb2            2551       38913   292085797+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdc2            3188       14596    91642792+   7  HPFS/NTFS

Disk /dev/sdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2442    19615333+  83  Linux
/dev/sdd2            2551       15017   100141177+   7  HPFS/NTFS
/dev/sdd3            2443        2550      867510    5  Extended
/dev/sdd5            2443        2550      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

edit: clarified.

---

### Post by Echo5ive on 2007-05-15
...and some further googling reveals plenty of problems installing linux with an Asus P5B motherboard, which is exactly what I have.

edit: My optical drive is an IDE, but connected via an IDE-to-SATA converter. Installing isn't a problem, it's grub getting confused when booting.

---

### Post by psusi on 2007-05-16
Which of those disks is your bios configured to boot from?  Also what does your /boot/grub/menu.lst look like, and did you get the grub error before the menu or after choosing to boot?

---

