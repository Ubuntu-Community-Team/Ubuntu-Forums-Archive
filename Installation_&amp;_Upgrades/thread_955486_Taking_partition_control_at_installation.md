---
title: "Taking partition control at installation"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2008-10-22
This is not the case, but please respond to it as if it were. One has 8.04 live CD in hand and the HD is completely NTFS not partitioned. One also has a gparted live CD.
What sequence or moves would one take to arrive at this partitioning:
hda1    pri    NTFS     Windows
hda2    pri    ext3     Ubuntu
hda3    pri    ----     Linux swap
hda4    ext    ----     extended partition
hda5    log    ext3     Linux /home
hda6    log    FAT32    data exchange

Now the real world and what actually happened with all the corrections I attempted.[http://s427.photobucket.com/albums/pp352/76yrold/](http://s427.photobucket.com/albums/pp352/76yrold/)
I guess stated another way is should I have partitioned first leaving that unallocated space in ext3 and applied installation then!

Thanks 

Allen

---

### Post by mikewhatever on 2008-10-22
Lets get straight with the terminology. If an HDD or a partition have a file system (could be ntfs, ext3 or other), it means it is partitioned, and the partitioned space is formatted and allocated.
In order to get an HDD the way you described, you have to manually partition it with Gparted or Ubuntu live cd. If all the space is un-allocated (no filesystem of any kind), simply create partitions of desired size and format. If all of the space is formatted as one big ntfs partition, you need to shrink it to the desired size, and then, create all the other partitions inside the unallocated space. Hope it makes sense.

---

