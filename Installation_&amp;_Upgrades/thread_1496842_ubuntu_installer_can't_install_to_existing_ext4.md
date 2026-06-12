---
title: "ubuntu installer can't install to existing ext4"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by deaddy on 2010-05-29
Hi there,

I haven't used linux for a long time, after this break i wanted to install ubuntu and give it a shot but altough that i have a 10gb free space and another seperate 2gb free space for a possible linux setup, installer can't seem to recognize them.

Any thoughts guys?

---

### Post by darkod on 2010-05-29
If you have the maximum 4 primary partitions, or 3 primary + extended, it ignored the free space because it can't create 5th partition in it.

Are you trying to use one of the guided methods or manual (advanced) partitioning also doesn't show it?

PS. If you can boot ubuntu in live mode (Try Ubuntu option) and open Gparted (System-Administration) and make a screenshot of the disk, the picture will say a lot. :)

---

