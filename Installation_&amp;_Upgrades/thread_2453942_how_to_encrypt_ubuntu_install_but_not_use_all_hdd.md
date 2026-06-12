---
title: "how to encrypt ubuntu install but not use all hdd?"
date: 2020-11-19
forum: Installation &amp; Upgrades
---

### Post by jebi on 2020-11-19
hi

how do i do an install of ubuntu or any linux for that matter using lvm encryption but not using all the partition?


say lvm encryt the file system 250GB
separate lvm 500gb data partition
and 250gb vfat for clonezilla backups

thx

---

### Post by TheFu on 2020-11-19
LVM doesn't do encryption. It is just a way to organize storage and make parts of that organization available as logical volumes which are used to place file systems. Encryption happens outside LVM.  Search the LVM manpage and there isn't any reference to encryption at all.

Typically, the LVM organization is placed inside an encrypted container or on an unencrypted partition. 
Any "file" can be an encrypted container and on Unix-like systems, almost everything is a file, unless it is a process.  You can make a file of any needed size using many different techniques (dd, cat, cp, truncate, fallocate, whatever ...). Then you can create an encrypted container inside that "file."

Typically, a partition is the smallest "file" used to hold an encrypted container, so if you want something smaller, make a smaller partition would typically be the answer. This would avoid overhead caused by having a file system.  I suppose you could setup LVM on a partition, then create a PV, VG, and multiple LVs ... with 1 LV being used as a block device (i.e. "file" for an encrypted container, then you could put a file system into that container.  I've not seen this, but it should work.

LVM is a process - LVM uses storage objects called 
[LIST]
[*]PVs, physical volumes, which hold ... 
[*]VGs, Volume Groups, which hold 1 or more ... 
[*]LVs, Logical Volumes
[/LIST]https://www.programmersought.com/article/9530199566/ I like the diagram about 10% from the top which shows 1 VG in the middle with multiple PVs and multiple LVs tied to it. Probably best to ignore the rest of that page. Just that 1 diagram is good.

Usually an LV is where a file system is laid down. We use **sudo mkfs -t ext4  /dev/mapper/{vg-name}-{lv-name}** to place an EXT4 file system onto an LV that is part of a VG.

A PV goes to a VG, but a VG can have multiple PVs.
An LV comes from a single VG, but a VG can (and should) have multiple LVs.

But if you place backups on the same disk, outside the encrypted container, you've just defeated the purpose for having encryption AND for having backups, right?

I must be missing something important.

---

