---
title: "Filesystem overhead"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by IcarusR on 2007-01-20
Hi all
I have just fitted a 3ware 8006-2LP raid card with 2 320 Gb drives in mirror raid into my server to store mP3's for my squeeze box.
Having partitioned & formatted the raid ext3 I have 298 Gb of free space. So the filesystem overhead is equal to 20 Gb.
I know there are several others, XFS, Reiser, JFS would any of these use up less space & be as reliable as ext3 ???

Thanks

---

### Post by esaym on 2007-01-20
I think I saw a chart one time and ext came out pretty good vs overhead.  Maybe the inode/block size got screwed up or defaulted to a large value due to such a large disk?

Also 5% of the disk is reserved so that if the disk is full you will still have root write access.  5% is the default.  

see: [http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

Looks like you can just do tune2fs -m1 on the unmounted drive and that will change the reserve from 5% to 1.

imo you can't really get any better then ext3

---

