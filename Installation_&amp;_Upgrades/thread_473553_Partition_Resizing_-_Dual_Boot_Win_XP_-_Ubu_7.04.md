---
title: "Partition Resizing - Dual Boot Win XP - Ubu 7.04"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by kerneld2000 on 2007-06-14
Hello,
I have installed Ubuntu 7.04 on my main pc and now I'm with a dual-boot system (win xp sp2/ubu 7.04). A minor mistake however meant an incorrect allocation of hard disk space and now I have a 40GB win xp partition (ntfs) and an 80GB ext3 ubuntu partition (on my Seagate 120GB drive), when I actually needed the opposite, since I use windows more.

Is there a safe way to resize my partitions and increase the ntfs partition to, say 80GB and decrease the ubuntu partition to 40GB without formating/reinstalling everything?

Thanks

---

### Post by ajgreeny on 2007-06-14
Use the gparted live CD to do all of what you want.  I've recently done the opposite, increased my ubuntu partition and decreased the WinXP partition.  This even meant moving the ubuntu partition backwards on the disk, something which used to be impossible, but not any longer.
So just fire up the gparted live CD (preferably not the ubuntu live CD as gparted on that is an older version, I think) and first decrease the ubuntu partition, then increase the winXP partition.

Good luck.

---

