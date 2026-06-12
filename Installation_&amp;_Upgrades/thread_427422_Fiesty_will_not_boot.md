---
title: "Fiesty will not boot"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by hemiT on 2007-04-29
Base Info:
Amd Athlon 2800+
2x 80 Gig Sata Drives on a SIL3112 sata controller, NO Raid
1x250 gig IDE drive.

Installed fiesty on one of the 80gig sata. Rebooted with out the cd, system gets to verifing DMI pool, then nothing.
System recognizes all drives from a hardware stand point, I know all drives work cuz I acronis the system back to xp and it works fine. 

Grub appears to not load.

any suggestions?

---

### Post by bulldog on 2007-04-29
If GRUB is not appearing when you boot,it's possible it's installed on the other hdd.
Try to boot from the other hdd to see if grub is installed there.:)

First guess would be the IDE hdd,however

---

### Post by hemiT on 2007-04-29
good call. Ubuntu installed on the sata a drive, sata b is not visible, and the ide is visible,
but I set the system to boot from IDE 0 in the bios and it booted up. Now the IDE drive is partitioned with NTFS, can I safely reformat this drive with ext3?
And can I make the 2nd sata visible?

---

### Post by bulldog on 2007-04-29
Can you boot the live cd and perform the next command in a terminal and post the output on the forum?
```
sudo fdisk -l
``` it's a lowercase L not a one :) 

You already installed Feisty,why would you do it again?
But if there's nothing of concern on the IDE hdd,no precious data or what ever,yes you can safely create new partitions and format them ext3.
But if there's a windows OS you'll better wait a minute.

---

### Post by hemiT on 2007-04-29
well im posting from fiesty now. There is no important data in the ide drive. 
The second sata I would like to view and format for storage as I would like to do with the IDE drive.

---

### Post by hemiT on 2007-04-29
here is the fdisk info

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by bulldog on 2007-04-29
Well if you want to install Feisty on the IDE hdd,be my guest :) 
Some advice,

Create a 10GB partition for /  [root]format it ext3 
Create a 1GB partition for swap format it as swap
Create a partiton for /home as big as you want,this one will have all your personal files and data.format it as ext3

You could create a fourth partition for additional data if you like,but I let this up to you.

Install GRUB on the IDE hdd and set this hdd as the master boot device in your BIOS.

EDIT;
if there's no important data on the sdb hdd,you can try to partition it again and format the partition,maybe this will make the hdd usable again.
You can use the gparted live cd to get a graphical partitioner [55MB download]
Burn the ISO to a disk and boot from it.
It's much more clear how your partitions are setup with this tool.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by hemiT on 2007-04-29
no I want it installed on the sata drive. 

What I want is:

partition the 250gig ide and the 80 gig sata. If I could make them my Home location that would be cool as well. Can I combine them under the home directory?

---

### Post by bulldog on 2007-04-29
You have to explain a little more what your goals are.
You can have just one partition as /home,it doesn't matter how many GB it is,you can't combine two disks to one  /home.

You need a  / partiton which contains all the ubuntu files,make this partition 10GB ext3
You need a swap file,make this 1GB.
The other partitions you can create as you like,just mount them on the place you want to see them.

---

