---
title: "Install 8.10 ( #4 ) partition"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Flag on 2008-08-25
I'm a bit hesitant installing.
I have: sda1 swap, sda2 25 gig = 8.04, sda3 60 gig = home, sda4 25 gig, formatted ext3, would like to install 8.10 alpha4 on this one. When I start installer all is normal till I hit the partitioner, it claims all partitions to be 0 in size,now I 'm wondering if I have to set the sizes of the different partitions to the right size manually, ignore it and just use sda4 for boot and sda3 for home.
Would hate to loose my current installation on sda2 and my home on sda3.
Thanks

---

### Post by Manosdoc on 2008-08-25
There is a bug in the partitioner GUI, not displying (like Hardy did) the spaces right.
Fill a bug at Launchpad !

---

