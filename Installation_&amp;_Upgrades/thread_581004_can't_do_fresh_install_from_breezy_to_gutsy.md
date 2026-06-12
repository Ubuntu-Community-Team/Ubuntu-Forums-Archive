---
title: "can't do fresh install from breezy to gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mluria on 2007-10-19
Trying to install ubuntu on old computer. Had old breezy disk, figured I could upgrade, but I see it's just better to do fresh install.  I don't have user files on disk.  

Downloaded new gutsy install, put on disk.  I basically want to erase everything on the disk and start over.  (Like I did with the old XP install).  Just can't figure out how to do it.  It just boots up normally into breezy.

I'm sure it's a simple thing, any help will be appreciated.

m

---

### Post by LLauranzonIII on 2007-10-19
i would first use dban to wipe the HDD clean.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

then after it's done restart and go in to BIOS and make sure CD is the 1st option for boot.  stick the disc in and you should be all set.

---

### Post by Desd on 2007-10-19
How about me, I am on a dual boot... DBAN will wipe my other OS partition. Any advice?
Thanks!


Desd

---

### Post by Topsiho on 2007-10-19
If you did it correctly you would not be able to boot into Breezy as that would not exist anymore. During the install (in stead of Breezy) you should set the mount points correctly and have the partitions for / (and /boot if you have that) formatted. If you have a /home partition you should have this mount point set and NOT have this partition formatted. That is the way to keep your personal files and settings.
Do not forget a swap partition, about two times your working memory space (I mean that of your computer, sorry :) )

Success with trying again.

Topsiho

---

