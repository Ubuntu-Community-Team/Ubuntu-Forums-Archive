---
title: "wubi free space"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by rcarm on 2008-02-09
i'm trying to install ubuntu 7.04 using wubi, everytime i run it i get message saying that i don't have enough free space and that 4gb are required. but i still have 4.80gb of free space in my C drive. then i downloaded the 7.04 alternate cd. now my free space is about 4.13. why can't i install it?

---

### Post by sub2007 on 2008-02-09
It could be your filesystem. If you are on anything pre-Vista (ie XP) then unless you have specially converted your filesystem to NTFS (or selected it at Windows installation) then you will be using FAT32. 

Wubi puts all the operating system files (ie the traditional partition) into a single file. In FAT32 (which is the default in XP) you have an absolutely maximum filesize of 4GB (it may be less than that, it's certainly no more than that). I've run into roadblocks when using virtual machines on FAT32 on approaching 4GB - I didn't have a clue what happened but it just stopped working and only on researching found that it was in fact that the virtual disk had grown to bigger than 4GB.

So that might well be the problem, obviously an operating system requires a LOT of hard disk space (we have nearly filled 15GB on our Linux partition JUST with OS and programs).

---

### Post by rcarm on 2008-02-09
> **sub2007 said:**
> It could be your filesystem. If you are on anything pre-Vista (ie XP) then unless you have specially converted your filesystem to NTFS (or selected it at Windows installation) then you will be using FAT32. 

Wubi puts all the operating system files (ie the traditional partition) into a single file. In FAT32 (which is the default in XP) you have an absolutely maximum filesize of 4GB (it may be less than that, it's certainly no more than that). I've run into roadblocks when using virtual machines on FAT32 on approaching 4GB - I didn't have a clue what happened but it just stopped working and only on researching found that it was in fact that the virtual disk had grown to bigger than 4GB.

So that might well be the problem, obviously an operating system requires a LOT of hard disk space (we have nearly filled 15GB on our Linux partition JUST with OS and programs).

thanks. i'll try to convert it to ntfs

---

