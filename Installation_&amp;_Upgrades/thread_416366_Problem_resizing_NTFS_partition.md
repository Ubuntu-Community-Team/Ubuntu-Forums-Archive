---
title: "Problem resizing NTFS partition"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Episcopus on 2007-04-21
I am trying to install Fiesty onto a 40gb hdd with XP on it.  I want to shrink my XP partition and be able to dual-boot in case Fiesty doesn't play nice with things I need for school.  The partitioning tool won't resize my XP partition.  It isn't giving me an error other than saying that it couldn't resize the partition.  Does anyone have any ideas on how to fix this so I can use Ubuntu full-time and not just on my desktop?

Averatec 3200 Series Notebook
Windows XP
40gb HDD
512 DDR
AMD Athlon XP-M 2000+

---

### Post by jdong on 2007-04-21
There are unfortunately cases where the Ubuntu NTFS resizer is unable to handle resizing certain NTFS configurations, and it simply gives up.

You can try:

(1) The gparted livecd at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/). This has newer versions of the NTFS resizing tools
(2) A commercial package, such as PartitionMagic. These handle more types of NTFS configurations.

---

### Post by Episcopus on 2007-04-21
If there is no free and easy way to do it now, I will probably wait a few weeks and reformat the drive and have only a Fiesty partition.  I graduate on May 20 and won't have to worry about agreeing with anything at school after that.  At that point, I could throw an XP partition in my desktop, just in case.  I wonder if the Edgy install will work, and then I can upgrade from Edgy once everything is partitioned right.  Unless someone knows for sure that it won't work, I will try it tomorrow and report back.

---

### Post by jdong on 2007-04-21
Alright, cool. If the Gparted livecd can't do it, then Microsoft has won this round of how to confuse the heck out of Linux NTFS developers :)

---

### Post by Episcopus on 2007-04-21
gparted worked.  Thanks for the help.

---

