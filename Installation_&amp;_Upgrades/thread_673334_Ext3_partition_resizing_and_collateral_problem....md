---
title: "Ext3 partition resizing and collateral problem..."
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by sethedge on 2008-01-20
Hi guys,
I resized my ext3 partition giving it free space before the old partition. 
Obviously, I'm having boot problems... :-P
In order to make the resize I removed the journaling, transforming it in a ext2 partition: resize operation was ok, now the partition table is like I wanted to be.

Little problem... I start from grub the linux system and I obtain a warning of fsck saying that I have to check manually the partition... that is what I've done...

The following is what I obtained...

```
# e2fsck /dev/sda5

Pass 1: Checking inodes, blocks and sizes.
```

(then fsck loops me the following output, I always say "yes")
```

Group 5's inode table at 163xxx conflicts with some other filesystem block.
Relocate<y>?

```

(after the last yes of a long series, the following is printed..)
```
Error allocating 501 contiguous blocks in block group 5 for inode table: Could not allocate block in ext2 filesystem.
Restarting e2fsck from the beginning...
```

(and starts again...)

Somebody can help me? :confused:

---

