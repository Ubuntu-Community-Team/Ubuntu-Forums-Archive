---
title: "dual boot -- having brain malfunction"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Tayashlor on 2011-01-01
okay, yes, im a newbie, but i have done this before about a year ago, and now i cannot remember what exactly to do to make this work correctly.

i have an acer aspire one with a 250 gb hdd
the hdd is currently partitioned into two parts 
part 1 - 85 or so gb, has windows installed
part 2 - the rest which is currently unallocated.

i am trying to install ubuntu so that each has its own section and will dual boot

once in the ubuntu installation window, how do i set up the partition to achieve this?

i am trying to install ubuntu 10.10 netbook 

thank you

---

### Post by Tayashlor on 2011-01-01
i keep getting 

no root file system is defined.
please correct this from the partitioning menu

---

### Post by drs305 on 2011-01-01
> **Tayashlor said:**
> i keep getting 

no root file system is defined.
please correct this from the partitioning menu

When you select the partition you want Ubuntu installed on, you must also select "/" from the mount point drop down box. It's in the same area as the type of format and the format tick box.

---

### Post by Tayashlor on 2011-01-01
thank you so much.

---

### Post by lkraemer on 2011-01-02
Perhaps you want to read up on Dual Boot at this Site:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

And you will most likely need SuperGrub
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

I'd also suggest the Gparted LiveCD from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

lk

---

