---
title: "Install problem"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by willb003 on 2007-02-23
Hello all I am trying to install ubuntu on my laptop, I have an 80gig hard drive in a toshiba laptop with win. XP home already. I would like to keep windows and all of my old stuff, When I tried installing ubuntu, the partitioner told me to use ntfsresize to resize the current single partition smaller to make room but when i use it it says access denied. I tried su root but it just says access denied as well. Any help would be greatly appreciated, i would like to join the linux community.

---

### Post by Kateikyoushi on 2007-02-23
I would use gparted to resize the partition it is on the live disc, but would defragement the drive few times, in case the hibernation file or the swapfile is in the second half of the disc would disable them defrag and enable them again.

---

### Post by willb003 on 2007-02-24
When I use Gpartition it tells me there is a bad sector and to ckhdsk and to use ntfsresize and when i do that i get the access denied code again.

---

