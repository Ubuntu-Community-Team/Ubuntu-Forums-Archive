---
title: "NTFS Partition becomes Unallocated"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by kanaqsasak on 2011-04-22
Hello, 
I have a laptop with 500GB of hardisk.

Here is the picture of my partition:

[IMG]http://i1106.photobucket.com/albums/h363/kanaqsasak/Screenshot.png[/IMG]

sda1 and sda2 was one partition before, then I resize it to make some room for Windows XP installation.
sda6 was sda5 before I shrink sda1. and the unallocated space was sda6 before.
I really need some help. How to repair the unallocated partition so I can use it without losing any file in it?
I have so much important file in the unallocated partition. Thanks for your help.

---

### Post by LostFarmer on 2011-04-22
From a root terminal run 'testdisk' .  Do a web search to find ;testdisk's home page and read the How- To use FIRST.  You can install program in XP if preferred. I think it installed by default in Ubuntu but if not ues Symatic package manager to do so.

---

### Post by srs5694 on 2011-04-22
As LostFarmer suggests, TestDisk is probably the best way to go; however, before you resort to it, you might check to see if fdisk can see the partition:

```

sudo fdisk -lu /dev/sda

```

You'll see a list of partitions, something like this:

```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      192779       96358+  83  Linux
/dev/sdb2         1012095   625137344   312062625   8e  Linux LVM
/dev/sdb3          192780     1012094      409657+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

That's taken from one of my disks and isn't equivalent to what you'll see. If you see your "missing" partition in the output (probably as /dev/sda7), then post the fdisk output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to preserve legibility. There's a slim chance that there's something wrong with the partition table that's causing GParted to ignore the partition when it's actually present. If you don't see the missing partition, then go ahead and use TestDisk.

If you use TestDisk and then find that GParted doesn't see any partitions at all, you'll have to either manually correct the partitions using sfdisk or use my [FixParts](http://www.rodsbooks.com/fixparts/) program to do the job automatically. (TestDisk is known to occasionally create a particular problem that causes GParted to show a disk as empty even if it's got partitions, and FixParts can fix that problem.)

---

### Post by Gondrano on 2011-04-27
Hi, 

I do not know if this is the right thread... thought there is some arguments involved.
Yesterday I made a very silly thing, wanted to repartitioning via GParted my 320giga ntfs data external hard disk (more than half full) with ext4, but I end up in a mess. I attach a picture which better describe where I am now. 

Though the data should be untouched I still does not know how to access it for eventually temporally copy it in a new hard disk.

thanks for advices

ps I think I add a partition (another of the same size) to the only one partition ntfs.

---

### Post by Dutch70 on 2011-04-27
Gondrano

This is not the right thread. Please start your own thread so you and the OP can get help specific to your problem.

You should probably go to the Absoulute Beginner forum and click "new thread" on the top left if you want to get help.

---

### Post by Dutch70 on 2011-04-27
> **kanaqsasak said:**
> Hello, 
I have a laptop with 500GB of hardisk.

sda1 and sda2 was one partition before, then I resize it to make some room for Windows XP installation.
**sda6 was sda5 before I shrink sda1. and the unallocated space was sda6 before.**
I really need some help. How to repair the unallocated partition so I can use it without losing any file in it?
I have so much important file in the unallocated partition. Thanks for your help.

I'm not sure you're giving the correct information here. Shrinking sda1 will not effect the name of sda5 or sda6 as they are logical partitions, sda1 is a primary prtn.

I believe what you've done is somehow accidentally shrank sda6 which means your files are still there. 
You just need to grow it to full size again. 

I'm also thinking you've figured this out & that's why you haven't been back to check on it. ;)

Let us know when you do.

---

### Post by srs5694 on 2011-04-27
> **Dutch70 said:**
> I'm not sure you're giving the correct information here. Shrinking sda1 will not effect the name of sda5 or sda6 as they are logical partitions, sda1 is a primary prtn.

It sounds to me as if there was an unfortunate combination of two things:


[list]
[*]Out-of-order logical partitions (say, in on-disk order of 5 6 4)
[*]A bug in the partitioning software that caused the partitioning software to delete a logical partition because of the out-of-order partitions
[/list]


This is not unprecedented. The Windows Vista/7 installer is known to do this under certain circumstances, for instance.

---

