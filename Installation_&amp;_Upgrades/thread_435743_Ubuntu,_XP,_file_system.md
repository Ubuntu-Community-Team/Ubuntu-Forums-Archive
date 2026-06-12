---
title: "Ubuntu, XP, file system"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by croquagei on 2007-05-07
Hey Guys, basically i'm about to put together a new pc and plan on installing both Ubuntu and XP as a dual boot.

2 hard drives, 80GB for operating systems (partitioned down the middle) and a 320GB for storage for use by both XP and Ubuntu.

So onto my question:
For the larger (320GB) storage hard drive what file system should i use so that both XP and Ubuntu can read and write to it?

Options:
1. FAT32 - prefer to not use due to it not supporting files over 4GB

2. NTFS - unsure about negatives now, i know that many linux distro's used to have difficulty writing to NTFS only i'm unsure how much that has changed as of late.

3. ext2/3 - can XP read/write to a ext partition?

So can anyone give me some more suggestions on what file system i should use and add any more pros and cons that i haven't listed?

---

### Post by hal8000 on 2007-05-07
Linux can safely read and write to NTFS now with ntfs-3g. It comes installed with knoppix and I have used it many times to write, delete or remove viruses from windows systems.

80G is a lot of space for linux, as is 320G. I would be tempted to reserve some space on the 320G in case you want to try out more linux distros. I have a single 160G HD running  7 linux distros, FreeBSD, Solaris and XP.
I have to admit , I still cant decide which distro I like best so I work on them all. In my case I use a common ext3 partition to share data between the linux's FreeBSD and Solaris. XP cant read ext3 but this is not important in my case.

---

### Post by frigin_AL on 2007-05-07
What if I had:
80GB = 10Gb Windows + remaining for My docs... how do I install ubuntu without loosing win and leaving something for My docs?

Or shoudl I use the 69GB for linux? so many choices, not much time! :-s

---

### Post by alenis on 2007-05-07
XP can read/write ext partitions with a freeware driver

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It works well, although in my experience sometimes XP can't access ext partitions. In this case I have to restart windows and then it usually works.

---

### Post by Whiffle on 2007-05-07
I second ext3 w/ the fs-driver.  I've got that setup on 3 computers now and it works quite nicely.  Granted I don't use XP much anymore, but its never given me problems.  The only difficulty I've run into is that ext3 doesn't support the archive bit like ntfs, so if you're using a backup program you have to do it a little differently.

---

