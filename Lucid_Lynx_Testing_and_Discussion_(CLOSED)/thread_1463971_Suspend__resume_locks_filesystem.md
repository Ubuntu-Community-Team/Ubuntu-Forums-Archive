---
title: "Suspend / resume locks filesystem"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuartN on 2010-04-27
After resuming from suspend the root filesystem becomes remounted readonly, as described at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981) (and several other places), an error first introduced in Ubuntu 9.10.

I am reasonably certain that this is not a hardware error because it affects a number of identical Dell 1501 Inspiron laptops, but not other machines. The laptops ran Ubuntu 8.10 with suspend / resume without any problem. (And of course other people report the same or related issues).

Obviously no messages are written to a log on a readonly filesystem, and it has some orphan nodes on resume:
```
[    2.200106] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.670702] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
[    2.670708] EXT4-fs (sda4): write access will be enabled during recovery
[    7.830753] EXT4-fs (sda4): orphan cleanup on readonly fs
[    7.830764] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 400085
[    7.830866] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 400025
[    7.830884] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 399741
[    7.830901] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 399398
[    7.830917] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 399397
[    7.830933] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 398371
[    7.830950] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 391392
[    7.830967] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 389818
[    7.831015] EXT4-fs (sda4): 8 orphan inodes deleted
[    7.831019] EXT4-fs (sda4): recovery complete
[    8.399302] EXT4-fs (sda4): mounted filesystem with ordered data mode
```

---

