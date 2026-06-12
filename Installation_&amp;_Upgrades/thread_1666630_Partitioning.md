---
title: "Partitioning"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by aflyingturtle on 2011-01-13
I was wondering if when you partition the drive, If it will skip around the hard drive and partition only the free spots until you have the specified amount, or if it will star going at the back of the disk and just overwrite anything. Also, If it only partitions the free amounts, What happens if you try and partition a greater amount then there is free space?

---

### Post by darkdragn on 2011-01-13
It will prevent you from partitioning anything that is already in use. Even if there is 200G free on an NTFS partition, you can not use it unless you resize the partition, shrinking it then redefining partition boundaries. It cannot use non-contiguous space for a single partition, however if you have multiple partitions labeled as LVM you can combine them... kind of... By adding multiple lvm physical volumes to a data group, you can put them all together to create a single logical volume then format that. However you have to look at the limitations on primary partitions, if you are doing that. 
It is possible to use the simple gparted GUI to resize, move, create, or delete partitions, and it will not allow you to do anything illegal... lol, or rather try to do anything impossible.

If you need any help with anything PM me, and include the output of fdisk -l 

Ok?

---

### Post by srs5694 on 2011-01-14
Partitions are contiguous groups of sectors; for instance, sectors 100 to 5,000 or 2,048 to 7,232,798. A partition therefore cannot contain disconnected sets of sectors on the disk. Since most people partition (or re-partition) a disk very rarely, this usually isn't a big problem; you just set it up with partitions of the sizes you want and then forget about it.

If, however, you think you might need to change your partition configuration frequently, you could look into [Logical Volume Manager (LVM),](http://www.howtoforge.com/linux_lvm) which is a way to allocate disk space in a more dynamic manner. When using LVM, you don't need to worry about sector numbers or where on the disk different partitions exist; you just allocate space (in "logical volumes" rather than in partitions) from a pool of available sectors. This is a lot like allocating space in a filesystem for a file; you don't worry about the sectors that a file consumes; you just remember its filename. If you delete a logical volume, its space goes back into the pool, much like deleting a file causes the space it consumed to be made available again. A new logical volume could be composed of sectors from all over the place, but this wouldn't be obvious. It's not possible (barring a bug) to over-allocate from the LVM pool. The big downside to LVM is that it's more complex than the conventional partitioning. LVM is typically built atop partitions (called "physical volumes" in LVM-speak), so you first create one or more partitions to be devoted to LVM. You then combine these physical volumes into a volume group, and allocate space in the volume group to logical volumes. There are about 50 text-mode commands to manage all of this (although you can do a basic setup with just a handful of commands). There are a couple of GUIs that can simplify things and make the learning curve a bit less steep.

Unfortunately, Ubuntu doesn't make installing directly to LVM easy. (Fedora's much better at this, FWIW.) If you want to use it, be prepared for a bit of a learning curve. It can be done, and it's got advantages for certain configurations, but given Ubuntu's weak LVM support, it's not something I recommend for the average Ubuntu user.

---

