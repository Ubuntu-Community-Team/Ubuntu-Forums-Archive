---
title: "installation crashed - 2 ubuntu partitions"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by dublinmasif on 2010-11-10
Hi I was installing ubuntu earlier and it crashed, became unresponsive for over 20mins so i used ctrl alt f1 then used sudo shutdown now.

i then installed it again with no problems.

when i installed it the 2nd time it didnt let me select the partition it created the first time so now i have two ubuntu partitions.

i tried to use gparted to add the unallocated space back to my main drive but i cant really see how to do it.

from what i have read elsewhere i have to have the partitions "next to each other". can someone please explain how i move them so i can do that.

Cheers!

---

### Post by dino99 on 2010-11-10
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by sikander3786 on 2010-11-11
Please show us the output of

```
sudo fdisk -l
```

For resizing, this might help.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by dublinmasif on 2010-11-11
> **sikander3786 said:**
> Please show us the output of

```
sudo fdisk -l
```

For resizing, this might help.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       14725   107668583    7  HPFS/NTFS
/dev/sda4           14725       19458    38012929    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           16644       19022    19101696   83  Linux
/dev/sda7           19022       19130      873472   82  Linux swap / Solaris
/dev/sda8           14725       16548    14641152   83  Linux
/dev/sda9           16548       16633      686080   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by dublinmasif on 2010-11-11
Sorry this looks neater:
[g]("http://b.imagehost.org/0218/sudof.jpg")

[[img]http://b.imagehost.org/0218/sudof.jpg[/img]](http://b.imagehost.org/0218/sudof.jpg)

sda6 and sda7 were the partitions created when ubuntu crashed the first time.

This is a screen shot from GParted.
[[img]http://b.imagehost.org/0341/GPARTED.jpg[/img]](http://b.imagehost.org/view/0341/GPARTED)]

Not really too sure how move these partitions around like. but your help is greatly appreciated! :D

---

### Post by sikander3786 on 2010-11-12
2 ext4 partitions, 2 swap, doesn't seem good.

Boot into a Live CD, use gparted, delete sda6, sda7 and create a new partition.

It would not be easy to add that space back to sda8. You'll need to delete sda9 and then resize and re-create a Swap partition (please post back if you need instructions on that).

If it is a fairly new install, I would recommend you to delete just all the partitions. Except sda5? If it contains some important data and re-install.

---

### Post by dublinmasif on 2010-11-12
Hi I deleted the drives 6-9 but when i restarted it wouldnt let me start i and i was getting the grub rescue screen. i tried the different methods around this forum, using ms-sys but that didnt work, the i got a windows 7 repair cd but that doesnt recognise anything wrong. 

so i thought if i installed ubuntu again it might solve my problem but.....

when i go to install it it onyl wants to take space from my windows one and not the 35gb that i have free.

how do i get it to install there?

i created a swap partition and another partition to install it but i was getting the "no root file system is defined"

any idears what i should do now?

---

### Post by sikander3786 on 2010-11-12
Why did you delete sda8 and sda9? They were the root and swap partitions. I had mentioned to delete sda6 and sda9 only. Sad for your troubles.

Now for reinstallation, did you look under the Manual partitioning option? It should list the unallocate space. You need to create at least 2 partitions there. '/' The root partition and the Swap partition.

You'll need to set one of the newly created partition's mount point to '/' in order to define a root file system.

---

### Post by dublinmasif on 2010-11-12
Oh crap, didnt really read it correcty.

firstly apologies for the spamming pictures. i cant edit teh pic here on the live cd.

ok so i made 2 partitions from the unallocated space, ext4 and a swap

[[IMG]http://b.imagehost.org/0904/Screenshot-1.png[/IMG]]("http://b.imagehost.org/view/0904/Screenshot-1")

but then i get the following error message

[[IMG]http://b.imagehost.org/0864/Screenshot-44.png[/IMG]]("http://b.imagehost.org/view/0864/Screenshot-44")

Do i have to change the boot loader or is there anything else i am missing?

---

### Post by sikander3786 on 2010-11-12
Select sda6, click Change... and set Mount Point to '/'.

Don't need to change the bootloader device.

---

### Post by dublinmasif on 2010-11-12
Ah delighted mate, thats working now.

i will report back now after its installed. hopefully that will sort out the problems with the grub!

---

### Post by dublinmasif on 2010-11-12
> **sikander3786 said:**
> Select sda6, click Change... and set Mount Point to '/'.

Don't need to change the bootloader device.

ah your a legend! Cheers that worked a beaut!

---

