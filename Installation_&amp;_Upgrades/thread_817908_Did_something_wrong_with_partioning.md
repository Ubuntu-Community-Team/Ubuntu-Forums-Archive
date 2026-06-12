---
title: "Did something wrong with partioning"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by clarkyscored on 2008-06-04
I kept stuffing up my installation of Ubuntu and I've installed it three times in as many days. Now I think I have three different Ubuntu partitions still present on my HDD. Obviously I'd like to get rid of them and keep just one with my windows partition. 

So I went into my windows partition thing and it shows this...


[IMG]http://i8.photobucket.com/albums/a26/g-drive/Untitled-3.jpg[/IMG]

Does this mean I have three unnecessary Ubuntu partitions? It would make sense, because I've reinstalled three times... I don't want to delete anything, because last time I stuffed up the grub client, which is another reason I had to reinstall..

---

### Post by lisati on 2008-06-04
From the Live CD you can use the Partition Manager (Gparted) to delete the partitions you don't want/don't need and to resize the ones you want to keep.

---

### Post by clarkyscored on 2008-06-04
> **lisati said:**
> From the Live CD you can use the Partition Manager (Gparted) to delete the partitions you don't want/don't need and to resize the ones you want to keep.


Last time I did that, they wouldn't delete properly. Also when I did that, the grub thing stuffed up and I couldn't get into anything. Is there another way other than using the Ubuntu partioner? Windows perhaps?

---

### Post by clarkyscored on 2008-06-04
Anyone at all?

---

### Post by Sef on 2008-06-04
1) Don't bump unless 24 hours have gone by.  Otherwise you could be given an infraction.

2) It appears that you have too many primary partitions.  Could you do this command from the Live CD:

Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` Small L

then copy and paste the results here.

---

### Post by clarkyscored on 2008-06-04
> **Sef said:**
> 1) Don't bump unless 24 hours have gone by.  Otherwise you could be given an infraction.

2) It appears that you have too many primary partitions.  Could you do this command from the Live CD:

Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` Small L

then copy and paste the results here.


Sorry mate, I just want to get this sort ASAP, because I have exams soon.

Ok, this is the outout.

```
michael@michael-desktop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:19:db:a5:89:85 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Network controller 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 4 
       bus info: pci@0000:04:04.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=32 


michael@michael-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
michael@michael-desktop:~$ sudo dhclient if_name 
There is already a pid file /var/run/dhclient.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

SIOCSIFADDR: No such device 
if_name: ERROR while getting interface flags: No such device 
if_name: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
michael@michael-desktop:~$ 

michael@michael-desktop:~$ 





```

---

### Post by clarkyscored on 2008-06-04
Sorry!

Meant this!

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf4b025b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072383+   7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           45218       46826    12924229+  83  Linux
/dev/sda6           46827       46903      618471   82  Linux swap / Solaris
/dev/sda7           46904       48641    13960453+  83  Linux
/dev/sda8           43583       45142    12530637   83  Linux
/dev/sda9           45143       45217      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2050 MB, 2050560000 bytes
64 heads, 32 sectors/track, 1955 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1956     2002160    6  FAT16
```

---

### Post by clarkyscored on 2008-06-05
Bump

Any ideas at all guys?

---

### Post by dstew on 2008-06-05
I assume you want to install Ubuntu Desktop 8.04 from a Live CD onto your /dev/sda disk. Is that correct? If so, you should probably delete the partitions /dev/sda5 through /dev/sda9 and create two new partitions out of the resulting unallocated space, one swap partition of about 1 Gb, and use the rest for the Ubuntu root partition, format ext3, mount point /.

Sometimes I find it easier to create the partitions before I run the installer, just to have them ready to go. You can do this on the Live CD, run the Gnome Partition Editor (GParted) from the System --> Administration menu, I think.

Note that in order to partition the hard disk, it cannot be mounted. That is, if the hard disk is showing up on your Live CD desktop, you need to right click and unmount it before trying to partition it.

---

### Post by Topsiho on 2008-06-05
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072383+   7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           45218       46826    12924229+  83  Linux
/dev/sda6           46827       46903      618471   82  Linux swap / Solaris
/dev/sda7           46904       48641    13960453+  83  Linux
/dev/sda8           43583       45142    12530637   83  Linux
/dev/sda9           45143       45217      602406   82  Linux swap / Solaris

These results do not tally with that of your Windows partitioning program, which showed nonsensical results anyway. One can not have more than 4 primary partitions on one disk.

You have here one primary partition, which is huge, and probably contains all of your Windows (sda1).
Next you have an extended partition (sda2), which is only a container for the other, logical partitions, sda5, sda6 etc.
Of these two are swap partitions, where only one is needed, and three are regular Linux partitions, probably ext3 (I have no table handy to find out what 83 exactly stands for).

What you can do is, using the liveCD of Ubuntu, ***or of GParted***, is to delete the partitions sda5, sda6, etc, so creating one unallocated space on your hard disk, and install Ubuntu on that.

Best thing is to plan this first, and then create three partitions manually when installing: first a swap partition which is twice as large as your RAM (the working space on your computer), one for the root partition (/), 6 to 10 GB (this is very ample in my situation), and one for your /home, using the remainder of the space. The larger /home is the more personal files it can contain.

OK, best is to try this out on a spare computer if you have one and then do it on your "production"computer. It's really easy if you have done it a few times....

Good luck,

Topsiho

---

### Post by clarkyscored on 2008-06-05
Thanks heaps for the feedback guys.

I think I forgot to mention that I have a perfectly working version of Ubuntu working, which I would like to keep. I also have a version that isn't working, because the video card drivers are all wrecked and some leftovers from another installation. I want to get rid of the unecessary ones and keep my good Ubuntu. The problem is that I don't know which partition is my good Ubuntu. The sizes of the partitiions on GParted conflict with HDD size on workin Ubunut. Is there anyway to tell which one I should delete?

Cheers

---

### Post by dstew on 2008-06-06
The surest way to figure out which is your working Ubuntu is to look at the kernel root parameter in your grub menu. To do this, at the grub menu, highlight the menu item that is your working Ubuntu, and press 'e' for edit. Look at the kernel line, and note the id of the disk that is designated as root on the kernel line. It might be /dev/sda6 or it might be a UUID number. If it is a UUID number, then you can check which partition it is by using the **blkid** command.

---

