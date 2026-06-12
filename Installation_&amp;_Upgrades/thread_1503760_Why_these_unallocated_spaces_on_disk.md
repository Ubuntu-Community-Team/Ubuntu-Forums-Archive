---
title: "Why these unallocated spaces on disk ?"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by moon_raker on 2010-06-07
I installed last month using manual partitioning from the live cd and saw only today that I have these 2x 1MB unallocated spaces as shown in the screenshot. A notebook where I used the same manual partitioning method also has this. Any ideas ? I certainly don't want to reinstall as all is fine on both machines.

---

### Post by zvacet on 2010-06-07
Download [Gparted live cd]("http://gparted.sourceforge.net/") and with it expand your existing partition to the left and to the right on unallocated space.

---

### Post by efflandt on 2010-06-07
10.04 by default aligns partitions differently, on 1 MB boundaries, instead of just on cylinder boundaries.  That can break some systems (like my older desktop with Asus mobo), but you can change that if you want to with **partman/alignment=cylinder** kernel boot parameter.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

Although, I still cannot figure out why I cannot boot from from an ext3 partition on the far end of a 500 GB USB drive on that problem PC (grub rescue error: unknown filesystem).  When using the above boot parameter to install, it is able to boot a 160 GB USB drive and from farther out on its 200 GB internal drive.

---

### Post by moon_raker on 2010-06-07
> **efflandt said:**
> 10.04 by default aligns partitions differently, on 1 MB boundaries, instead of just on cylinder boundaries.  That can break some systems (like my older desktop with Asus mobo), but you can change that if you want to with **partman/alignment=cylinder** kernel boot parameter.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)



That makes sense to me, thanks efflandt. I will just leave as is.

---

### Post by totemtigger on 2010-06-13
> **efflandt said:**
> 10.04 by default aligns partitions differently, on 1 MB boundaries, instead of just on cylinder boundaries.  That can break some systems (like my older desktop with Asus mobo), but you can change that if you want to with **partman/alignment=cylinder** kernel boot parameter.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

Although, I still cannot figure out why I cannot boot from from an ext3 partition on the far end of a 500 GB USB drive on that problem PC (grub rescue error: unknown filesystem).  When using the above boot parameter to install, it is able to boot a 160 GB USB drive and from farther out on its 200 GB internal drive.
thanks efflandt.  I also was curious about this but not enough to ask.

---

