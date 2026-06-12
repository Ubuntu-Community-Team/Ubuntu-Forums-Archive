---
title: "min free space for different partitions"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by celsiusat on 2012-06-22
Hi all,

In the windows world we know that if system partition doesn't have enough free space , O.S will start to have major issues , there should be free space of at least 1 G.B. 
in the same lines what is the minimum required free space for different partitions in Linux (i.e /, /usr, /var,/opt, /tmp etc ) ??
can any one give a general guide line as on how many % of root partition, % of /usr , %of /var.... should be left free ?

---

### Post by dino99 on 2012-06-22
the system itself deal with subdirs, so you only need to let 10-15% of free space on / (root)

when manually installing, usually we set:
- / 12-15 Gib
- swap  min2 Gib and min 4 Gib if you plan to use resume/hibernate
- /home no limit but as much as you can.

---

### Post by celsiusat on 2012-07-04
is there any other empirical rules ?

---

