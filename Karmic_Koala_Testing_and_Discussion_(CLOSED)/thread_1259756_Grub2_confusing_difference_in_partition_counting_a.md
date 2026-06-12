---
title: "Grub2: confusing difference in partition counting and device counting"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Pjotr123 on 2009-09-06
In Karmic, Grub2 will be installed. The successor to the current Grub.

Grub2 still has a nasty bug. Partition counting starts at 1. However, device counting starts at 0 (the old method). This difference is very unwise and will cause needless confusion.

Counting of partitions and devices should be exactly the same. Both of them should start counting at 1, or both of them should start counting at 0 (old method). No mix.

I've filed a Launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425421](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425421)

Please feel free to support it there. Maybe there is still time to change this before Karmic arrives. :)

---

### Post by presence1960 on 2009-09-06
That is strange because I have GRUB 2 with sabayon 4.1 and counting or numbering for both devices & partitions remains the same as GRUB 0.97 where UUID is not used as in chainloading.

---

### Post by ronparent on 2009-09-07
Pjotr123 is right. It's explained here: [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+2)

---

### Post by presence1960 on 2009-09-07
> **ronparent said:**
> Pjotr123 is right. It's explained here: [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+2)

I only said it was strange not incorrect.

---

