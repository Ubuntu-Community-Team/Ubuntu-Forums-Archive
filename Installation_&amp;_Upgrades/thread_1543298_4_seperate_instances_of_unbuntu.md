---
title: "4 seperate instances of unbuntu?"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by m138 on 2010-07-31
i recently installed xubuntu on a pc, its got a pretty small hdd - 40 gigs. So xp is on there and its like 8 gigs. xubuntu said it would be 3 gigs... after getting a number of upgrade files i see that there appears to be 4 versions of xubuntu
1) 10x.24 
2)10x.24 (recovery mode)
3)10x.21 <- i think this was the iso that i downloaded
4)10x.21 (recovery mode)
 
so after doing the install i have only 433 megs left and i didnt install anything of my own choosing, just the updates. I want more space and im not really use to the interface yet - so am I correct in assuming i've got 4 versions on the hdd? if so how do i get rid of the extras to conserve space?

---

### Post by tgalati4 on 2010-07-31
No, you only have 2 kernels.  The kernels use up about ~12 megs each.  Look in /boot.  You can boot into normal mode or recovery (text terminal) for each kernel.  You normally want to keep at least one backup kernel.  Sometimes updates break things and you can boot into your previous kernel if you experience problems.  It's rare but it does happen.

You need to get a bigger disk.

Or delete Windows.

---

