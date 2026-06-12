---
title: "Dual booting Windows 7 and Ubuntu 9.10"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by rich5665 on 2009-12-03
I want to dual boot Windows 7 and Ubuntu 9.10. I have a new Dell Inspiron 1545 that has Win7 installed. The hard drive is 500GB, I have repartitioned the drive and created a 120GB partition for Ubuntu to be loaded on. When I start the install process Ubuntu can see the new partition but wants to install on the partition the contains Windows. I went to use the advanced option in the Ubuntu Partition Utility and selected the free space for Ubuntu.
At this point I'm a bit, I'm a bit confused as to how continue at this point.

---

### Post by darkod on 2009-12-03
You say you created a 120GB partition. If you did this from within windows, and you actually did create a partition, Ubuntu installer will consider it is unavailable. You need free unpartitioned space. Easiest to create that is to just delete that 120GB partition.
Then in the ubuntu installer you can select Use Largest Continuous Free space as option.
If you really want to create your partitions manually we can give instructions but you will have to delete the 120GB also and create partition into the free space created by that.

---

### Post by rich5665 on 2009-12-03
Sorry. I meant to say 120GB of free space. Although Ubuntu sees the free space, it wants to install onto the Windows Partition in the standar install method. I'm not very familiar with the advanced options with Ubuntu so you'll have to bear with me a bit. I've selected the free space then clicked add. The partition size as indicated will be 125989MB. If the free space is only 117GB then how can there be 125GB available for the new Partition. 

Do I want to make it a Primary Partition or leave the default at Logical?

The second drop down has "Ext4 journaling file system", should I leave it at the default setting?

Should the location be the beginning ot the end and what should the mount point be? I was going to use "/home".

---

### Post by darkod on 2009-12-03
OK. 1GygaByte has 1024 MegaBytes, not 1000, that's why the discrepancy.
I prefer manual partitioning always. I do not know how many primary partitions you have but it's better to put it on logical anyway. So...
**Yes, leave the choice as logical for all partition that you will create now.**
You will need 3.
/ (root) (something like C: in windows, system partition)
/home (better to be separate if you want to reinstall you keep the personal files)
swap

You have 120GB to dedicate, that's great. Root doesn't need more than 20GB, remember ubuntu is not demanding for the system partition as windows is. For comparison, the default win7 Ult install is 17GB, ubuntu desktop install is 2.7GB. :)

My advice:
Partition1:
Filesystem Ext4
Size 20GB (or 21475 MB calculated in millions of bytes, note the box says 1000000)
Select at beginning of free space
Mount point /

Partition2
Filesystem Ext4
Size Remaining - swap
Select beginning
Mount point /home

Partition3
Filesystem swap space
Size All remaining
Mount point swap area

For swap, you need to decide before starting creating the partitions and calculate all three of them. You should have minimum 2GB swap, or usually at least the size of your RAM. If it's new system it probably has more RAM than 2GB so just make swap the same. That means for /home you will have the total free space - 20GB - swap.

You can play with the numbers, for example make root 30GB but I really think you don't need it. Or 25GB.

Hope this wasn't too confusing. Any questions, just ask.

---

### Post by rich5665 on 2009-12-03
Thank you for the help. This was the first manual install of the Ubuntu OS. In tha past I've always done a standard install on a clean drive.

---

### Post by darkod on 2009-12-03
No problem. You got it running already? :)

---

### Post by rich5665 on 2009-12-03
Quick and painless. That's why I like this OS. I don't think the install took more than half an hour. Again thank you for the help. Both Operating Systems started up just fine, the boot loader could be a little easier to follow, but over all a smooth install. This is my first Dual Boot system with Ubuntu, the last was Mandrake Linux a few years ago.

---

### Post by M!K3_$ on 2009-12-03
> **rich5665 said:**
> This is my first Dual Boot system with Ubuntu

congratulations.
live long and prosper!

---

