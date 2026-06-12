---
title: "Partition Plan on ThinkPad X60s Notebook"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by farang on 2007-06-02
Dear forum,

I'd appreciate if anyone could review my partition plan for an uncustomised ThinkPad X60s, a notebook PC.

The hard disc is partitioned currently as below (in the order of physical positioning):

[FONT="Courier New"]Use. . . . . . . . . . . .Format. . . . .Partition Type. . . . . .Size. . . . . . . . . . . . . .Drive Name/Letter?
WindXP Installation. . . .NTFS. . . . . .Primary. . . . . . . . . .what remains out of 80GB. . . hda1
WinXP Recovery partit. . .fat32. . . . . .Primary. . . . . . . . . .5GB. . . . . . . . . . . . . .hda2[/FONT]


I am planning to shrink hda1 and create three new partitions in the cleared space (in the order of physical positioning):

[FONT="Courier New"]Use. . . . . . . . . . . .Format. . . . .Partition Type. . . . . .Size. . . . . . . . . . . . . .Drive Name
WindXP Installation. . . .NTFS. . . . . .Primary. . . . . . . . . .20GB. . . . . . . . . . . . . .hda1
Feisty Fawn Inst. . . . . .Ext3. . . . . Primary. . . . . . . . . .20GB. . . . . . . . . . . . . .hda3
/home = shared files. . . .Ext3*. . . . .Logical. . . . . . . . . .what remains out of 80GB. . . .hda5
Swap. . . . . . . . . . . .Type 82 . . . .Logical. . . . . . . . . .1GB**. . . . . . . . . . . . .hda6
WinXP Recovery partit. . .fat32. . . . . .Primary. . . . . . . . . .5GB. . . . . . . . . . . . . . .hda2[/FONT]
*I will use [Ext2 IFS]("http://www.fs-driver.org/") on WinXP so I can get rid of fat32 for sharing between Win and Ubuntu.
**Memory size being 512MB.

I am glad to have any useful comments but I am particularly anxious to know if I have placed WinXP recovery partition (IBM_SERVICE) in the right position, drive name, order in relation to other partitions.

Thank you in advance,
F :D

---

