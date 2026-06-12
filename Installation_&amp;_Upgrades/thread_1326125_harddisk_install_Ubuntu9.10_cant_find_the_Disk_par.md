---
title: "harddisk install Ubuntu9.10 cant find the Disk partition"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by frantzsong on 2009-11-14
i don't have a cd-rom
so  i install ubuntu just by harddisk.

at the beginning, it go to the ubuntu live-cd mode desktop
and then , i  double-click the icon "install"

but when choose the disk ,ubuntu don't found my windows xp system.
it say ,there have no system, and also,it did not found my disk partition.

what should i do?

i want install ubuntu and xp
and  xp had installed before and keep it 

and install ubuntu in the D: partition.

---

### Post by mikewhatever on 2009-11-14
OK, you don't have a cdrom, so it's probably a netbook. Is it? Do you know which model? It might help to narrow the search for a possible solution. 
I am guessing you've made a live usb to run Ubuntu from, is that correct? And the problem is, that Ubuntu doesn't see your hard disk partitions, right?
Could you start Ubuntu again, go to Application->Accessories>Terminal, type in **sudo fdisk -l** , and post the output here.

---

### Post by frantzsong on 2009-11-15
> **mikewhatever said:**
> OK, you don't have a cdrom, so it's probably a netbook. Is it? Do you know which model? It might help to narrow the search for a possible solution. 
I am guessing you've made a live use to run Ubuntu from, is that correct? And the problem is, that Ubuntu doesn't see your hard disk partitions, right?
Could you start Ubuntu again, go to Application->Accessories>Terminal, type in **sudo fdisk -l** , and post the output here.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0b1ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    46347524    23172738+   7  HPFS/NTFS
/dev/sda2        46340096   107780084    30719994+   7  HPFS/NTFS
/dev/sda3       107778048   312592769   102407361    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.

---

### Post by samepaul on 2009-11-15
Try this :D

[http://ubuntuforums.org/showthread.php?t=1299005](http://ubuntuforums.org/showthread.php?t=1299005)

---

### Post by darkod on 2009-11-15
It doesn't look like the thread will solve this.
From the fdisk list it seems all of the hdd is shared by three ntfs partitions.
You need free SPACE to install ubuntu. By this, I don't meanfree space as reported by windows, that it only showing you how much free space you have on your windows partitions but whole of the hdd is still occupied by the partitions.

By the look of fdisk you seem to have three windows partitions, in windows called C, D and E probably. If you want ubuntu, you need to move all your data from E: for example, to other partitions or external drive, then boot with the ubuntu CD and select Install Ubuntu.

On the page asking where to install select manual partitioning and delete the partition you emptied, most probably it will be /dev/sda3. BE VERY CAREFUL when deleting it.

Depending which windows partition you want to "sacrifice", you will need to delete that partition during the ubuntu install. Once it is deleted, it will create free space for Ubuntu. You will have the option to use automated install or create / (root) partition manually.

---

### Post by darkod on 2009-11-15
If you need more detailed help, for a starting point go into XP and open My Computer.

Tell us how many drives (letters) you see there, what is the size of each of them and how much free space in windows you have on each.

If we know that we can give you recommendation but in the end you have to make the decision yourself.

PS. Also tell us how big is your hard drive in total. 160GB, 250GB, etc

---

### Post by samepaul on 2009-11-15
> **darkod said:**
> It doesn't look like the thread will solve this.
From the fdisk list it seems all of the hdd is shared by three ntfs partitions.
You need free SPACE to install ubuntu. 

> **frantzsong]install ubuntu in the D: partition. [/QUOTE]

[QUOTE=darkod said:**
> 
PS. Also tell us how big is your hard drive in total. 160GB, 250GB, etc

[QUOTE=frantzsong]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: **160.0 GB**, 160041885696 bytes [/QUOTE]


I think all questions are answered already

---

### Post by darkod on 2009-11-15
OK, I missed the 160GB part. :)
Apart from that, installing on D: won't work for Ubuntu. It's as simple as that.
Personally, I wouldn't install linux between two windows partitions but that it up to the OP.

---

### Post by mikewhatever on 2009-11-16
> **darkod said:**
> OK, I missed the 160GB part. :)
Apart from that, installing on D: won't work for Ubuntu. It's as simple as that.
Personally, I wouldn't install linux between two windows partitions but that it up to the OP.

I think the problem is not whether to install on D:\ or another partition, or the lack of unallocated space, as you suggested, but rather the fact, that the partitioning program does not see the existing partitions on the hard disk. Had it seen the partitions, it would have been possible to resize one of them and install Ubuntu, but since it doesn't, the OP can't pass the partitioning stage.
It's an odd bug, cause, obviously, fdisk can see the partitions with no issues.

---

