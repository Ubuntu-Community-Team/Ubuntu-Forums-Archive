---
title: "Setting up partitions and vista"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by nick1122 on 2008-10-13
So I've tried out the wubi version of Ubuntu and decided to install it properly with a separate partition.
My laptops hardrive is not partitioned at all, so vista and my data is all on the same drive.
Can I make a partition just for vista OS files, a partition for Ubuntu and a partition for my data, accessible from both OS's?
If so, how do I separate the vista OS files from everything else?

---

### Post by prshah on 2008-10-13
> **nick1122 said:**
> So I've tried out the wubi version of Ubuntu and decided to install it properly with a separate partition.
My laptops hardrive is not partitioned at all, so vista and my data is all on the same drive.
Can I make a partition just for vista OS files, a partition for Ubuntu and a partition for my data, accessible from both OS's?
If so, how do I separate the vista OS files from everything else?

You can transfer your existing Wubi installation to a dedicated partition; see [Help to Move to Full Time]("http://ubuntuforums.org/showthread.php?t=904182&highlight=lvpm")

Your Vista partition will remain accessible in Ubuntu; you can comment out the relevant partition line in /etc/fstab to prevent automatic access. This way, if you need to use it, you can still mount it manually when required.

Use Vista's partition manager to shrink the Vista partition; the rest of the partition allocations can be done from Ubuntu (including common partition).

You can use NTFS as your common partition since Ubuntu from 7.10+ includes out-of-box support for NTFS partitions.

---

