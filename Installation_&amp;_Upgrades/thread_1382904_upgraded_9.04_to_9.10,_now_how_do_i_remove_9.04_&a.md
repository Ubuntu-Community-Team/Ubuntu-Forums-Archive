---
title: "upgraded 9.04 to 9.10, now how do i remove 9.04 &amp; dual-boot?"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by alpacadaddy on 2010-01-16
Good Day All!

I have both 9.04 & 9.10 installed & running with a dual-boot...now I want to remove 9.04 and go to a single-boot of 9.10...how do I do this?

I want to reclaim my disk space from the old OS as well...to make matters alittle messier, 9.10 was installed first...then after encountering trouble I installed 9.04 to see if it solved my problem...when I figured out how to solve problem it worked same on both releases...so I now want to remove 9.04 and stay with 9.10...but I don't want the uninstall of 9.04 to impact the 9.10 install...I would also like to adjust the partitions so that I can use all of the disk for 9.10 (including that which was used for 9.04 and it's swap file)...I hope this makes sense :/

thanks for following my twisted logic!

phil

---

### Post by arnab_das on 2010-01-16
i dont think its possible ro reclaim the space u have on 9.04 without going for an all out format repartition.

you could keep those two OSes as is, until ur ready to go for the formatting and partitioning.

---

### Post by kansasnoob on 2010-01-16
> **alpacadaddy said:**
> Good Day All!

I have both 9.04 & 9.10 installed & running with a dual-boot...now I want to remove 9.04 and go to a single-boot of 9.10...how do I do this?

I want to reclaim my disk space from the old OS as well...to make matters alittle messier, 9.10 was installed first...then after encountering trouble I installed 9.04 to see if it solved my problem...when I figured out how to solve problem it worked same on both releases...so I now want to remove 9.04 and stay with 9.10...but I don't want the uninstall of 9.04 to impact the 9.10 install...I would also like to adjust the partitions so that I can use all of the disk for 9.10 (including that which was used for 9.04 and it's swap file)...I hope this makes sense :/

thanks for following my twisted logic!

phil

It depends on the partitioning. Could you post a screenshot of Gparted and explain which partition is which?

If you used the automated resize (side-by-side) you might have only one primary partition at the beginning of the disc and that could cause heartaches.

Let's take time to give this a look before doing something reckless.

---

