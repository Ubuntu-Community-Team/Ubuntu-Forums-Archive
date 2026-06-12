---
title: "Vista/dual boot/shared partition/partition order"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by gambrjl on 2008-04-13
Ok.  planning on dual booting my Vista laptop with ubuntu and want to share a partition between the two for music, video, files etc..  My thoughts were to use the [FS-Driver](http://www.fs-driver.org/index.html) and create a 50G or so "shared" partition between the two operating systems.  My question is should I have the partitions in any particular order?

Right now i've got a 120G HD with Vista on it.  I was planning on shrinking it down to 30 or so with vista's tool in the Administrative tools and then boot the Live CD and create the rest with the free space.  Should the shared portion come next so that Vista can "see" it or does that matter?

Should I do

Vista (30G)   |    shared ext3 partition (50G) |  Ubuntu Home (30G) |  Swap (4G)

and should they all be primary or should some be logical?  I'm not 100% on that either

TIA

---

### Post by Pumalite on 2008-04-13
1 GB of /swap is plenty. /swap=RAM in laptops. You can have your shared in the middle. I'dmake one extended partition and put the rest within it.

---

