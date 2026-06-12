---
title: "Did i install Hardy on NTFS?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by football68 on 2008-04-28
Im doing a dual boot with xp and hardy. When i installed hardy a selected ext3 for the partition. In xp I am trying to use the Ext2IFS tool to mount my ubuntu partition but it says that the partition is NTFS/HPFS. Why is this when i specifically chose ext3.

---

### Post by Monicker on 2008-04-28
You can't install Hardy on an ntfs partition.

Verify the partitions and their filesystems. From a terminal:

```
sudo fdisk -l
```

---

