---
title: "Resizing partition with TestDisk and GParted"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by j.biddy on 2011-02-10
I have been running flavors of Ubuntu on my desktop for some time now which has been amazing and I love every bit of it. Like many PC users I miss some games that are unplayable in Ubuntu so I'm trying to add an XP install to dual boot too. I have a 200 GB ATA hard drive (currently a dynamic windows disk) with data on half the disk that I wish to add a partition too. Apparently GParted can't deal with Windows Dynamic disks so I got an error from the program. I did a little research and found the program TestDisk which can backup data and rewrite the partition structure, which I tried to do. 

The plan was to change it to a basic disk and then resize with GParted. However, when I open GParted it sees the entire disk as unallocated space even though I can view all the contents that were previously on the disk if I mount it explore in a file manager. I'm scared to touch it in GParted for fear of messing up the disk something fierce. 

Any direction that could be provided is much appreciated.

**EDIT: ** I thought I would add some output from an fdisk command. I'm guessing that my partition is trying to extend beyond the physical drive, which I'm pretty sure I can fix with fdisk but am not quite sure how. 
> biddy@biddy-lorde-box:~$ sudo fdisk /dev/sdb -l -u

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, **total 390721968 sectors**
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf08964c0

   Device Boot      Start         **End**      Blocks   Id  System
/dev/sdb1   *          63   **390732929**   195366433+   7  HPFS/NTFS


---

### Post by srs5694 on 2011-02-10
You can delete the partition in fdisk and re-create it, but using a start sector of 63 and an end sector that's legal. The danger is that you really don't know how big the *filesystem* in that partition is. Of course, it shouldn't be bigger than the disk itself, so if you just max it out it should work; however, I'm concerned about the conversion from a Windows "dynamic disk" format to a conventional partitioning system via TestDisk. This works *if you're lucky,* but based on my limited knowledge of Windows dynamic disks, it could also end up corrupting your data.

Thus, my recommendation is that you mount the partition, copy all the data you want to preserve to another physical disk, unmount the partition, delete the partition, repartition the disk in whatever way you like, and restore the data you backed up. You might be able to resize the partition more directly, but if there's anything weird going on, you could end up trashing the disk. IMHO, it's better to back it up, repartition, and restore than to tempt fate by trying to resize the partition, even after you fix the obvious problem with the partition being too big.

---

