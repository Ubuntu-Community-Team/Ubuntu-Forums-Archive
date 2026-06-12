---
title: "HELP. Ubuntu 10.10 Installation (with 64-bit Windows 7)"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by jmschuaquico on 2010-11-26
Hi guys. Im new here (and a NOOB).

I need help installing Ubuntu 10.10 in my laptop with Windows 7 64-bit. The "Install alongside other operating systems" option does not show. Why is that? What am I supposed to do? TIA!

---

### Post by dino99 on 2010-11-26
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by jmschuaquico on 2010-11-26
Thanks dino99 for the link.

But the instruction is very short. What 3 partitions? What sizes for those 3 partitions? I only have 6GB unallocated memory. Will it be enough? After creating 3 partitions, what then? Sorry, a real noob here.

---

### Post by Quackers on 2010-11-26
If your hard drive is alreay filled with partitions (even if they are largely empty) there is no room for Ubuntu to install. You may need to create free space for Ubuntu.
It may be necessary to shrink a Windows partition to leave that free space. This can be done using Windows Disk Management tool ( Start > right-click on Computer then select Manage then in the window which appears click on Disk Management. Then you can right-click on the partition you wish to shrink and select "shrink".

---

### Post by dino99 on 2010-11-26
you cant do anything with 6 Gb free space on disk, you need to resize the winblows partition(s) to make room. (the link already give the details, take time to read it, each word is important)

---

### Post by sikander3786 on 2010-11-26
> I only have 6GB unallocated memory.

That would be a bit low for Ubuntu. The root partition needs to be > 8 GB in my recommendation and Swap should be RAM x 2. If you can't manage more space, forget about a separate /home.

If you could please post the output of this command from Live CD's Applications > Accessories > Terminal

```
sudo fdisk -lu
```

To let us figure out something else for you ;-)

---

### Post by jmschuaquico on 2010-11-26
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5ad88e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   223801343   111695872   42  SFS
/dev/sda4       223801344   625140399   200669528   42  SFS

This is the output of sudo fdisk -lu

I can shrink my windows partition and get about 20 GB unallocated space. Will that be enough? Say it is enough, will the "Install alongside other operating systems" option be available?

Thank you guys for the reply.

---

### Post by dino99 on 2010-11-26
again follow post #2, all is explained there.

---

### Post by sikander3786 on 2010-11-26
> **jmschuaquico said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5ad88e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   223801343   111695872   42  SFS
/dev/sda4       223801344   625140399   200669528   42  SFS

This is the output of sudo fdisk -lu

I can shrink my windows partition and get about 20 GB unallocated space. Will that be enough? Say it is enough, will the "Install alongside other operating systems" option be available?

Thank you guys for the reply.
No that output is not normal. You have got Dynamic Disks and you need to convert them to basic in order to install Ubuntu. Partitioning and Install alongside another OS would be the 2nd problem you encounter. SFS is the first one here ;-)

You need to use Windows 7 partitioning tool in order to convert those dynamic discs to basic. You need everything backed up before doing that. The official partitioning tool was intended to complete that operation without making you lose any data but back up is always a safer approach.

I haven't use that so can't advise any further. Might be some mate posts some helpful links.

---

### Post by Quackers on 2010-11-26
It seems that you may have tried to create a fifth primary partition, is that correct?

---

### Post by jmschuaquico on 2010-11-30
Is it possible to install Ubuntu with Dynamic Hard Disk?

---

### Post by sikander3786 on 2010-11-30
> **jmschuaquico said:**
> Is it possible to install Ubuntu with Dynamic Hard Disk?
Sadly, not yet. "Dynamic Partitions" is a Microsoft thing not yet supported in Linux.

You need to convert them to basic partitions in order to install Ubuntu/Linux.

---

