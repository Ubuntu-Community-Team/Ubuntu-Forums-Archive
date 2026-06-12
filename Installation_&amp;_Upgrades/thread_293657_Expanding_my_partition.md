---
title: "Expanding my partition"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by glaeven on 2006-11-05
This is what gParted look like

[IMG]http://www.buckusy.org/stuff/screenshot.png[/IMG]

my question is simple. how do i get /dev/hda3 into the unallocated space? :confused: 


(System info: 900mHz AMD Atalon (i386), 128Mb RAM, ~30Bg HDD, Wireless USB (Belkin F5D7050) adapter (slow...), Ubuntu 6.10 Edgy Eft)

---

### Post by dcstar on 2006-11-06
> **glaeven said:**
> This is what gParted look like
.......
my question is simple. how do i get /dev/hda3 into the unallocated space? .......

Not sure you can, it may be easier to create a new EXT2 partition, and use the **partimage** utility to make a copy of your existing partition and then copy it back into the new space.

You may have to do this in a couple of steps as you need some disk space that's big enough to hold the copy.

---

### Post by cotcot on 2006-11-06
This is possible because you have no overlap between the new location and the partition you want to move. It is even easy because it is your first partition you want you move to the front. As you do not jump over other partitions there will be no issue with partitions renumbering. From a liveCD in terminal use parted :

sudo parted /dev/hda

This will give you the parted prompt :
(parted) move 1 1MB and accept the proposed end point.

I am sure it works with parted, I have use this commnad multiple times. I am not sure wether you can start at zero because of the 512 kB space for MBR. That is why I propose at least 1 MB as starting point.

See : [http://www.gnu.org/software/parted/manual/parted.html#move]("http://www.gnu.org/software/parted/manual/parted.html#move")

---

### Post by hajo9702 on 2006-11-08
> **cotcot said:**
> This is possible because you have no overlap between the new location and the partition you want to move. It is even easy because it is your first partition you want you move to the front. As you do not jump over other partitions there will be no issue with partitions renumbering. From a liveCD in terminal use parted :

sudo parted /dev/hda

This will give you the parted prompt :
(parted) move 1 1MB and accept the proposed end point.

I am sure it works with parted, I have use this commnad multiple times. I am not sure wether you can start at zero because of the 512 kB space for MBR. That is why I propose at least 1 MB as starting point.

See : [http://www.gnu.org/software/parted/manual/parted.html#move]("http://www.gnu.org/software/parted/manual/parted.html#move")

I'm in a similar situation but my system has dualboot with Grub.
Can I simply copy my root partition (with no loss of data?) from /dev/hda3 to the unallocated space?

How do I update my menu.lst to boot from the new partition?

```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=85ae1b75-9a59-4ec4-95da-e15b813a3673 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

[IMG]http://nolaris.se/snapshot1.png[/IMG]

*CPU: AMD Athlon(TM) XP 2000+ Kubuntu 6.10 Edgy Eft*

---

