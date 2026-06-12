---
title: "/boot as ext2? Actual speedup?"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by mbsullivan on 2007-07-11
Hi All,

It's suggested [here]("http://ubuntuforums.org/showthread.php?t=498337&highlight=%2Fboot+partition") and [here]("http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/") that creating a separate partition for /boot as ext2 will speedup the boot process. I've heard this before, and I believe the theory is that journaling overhead is avoided in this case, which results in a (theoretical) speedup.

I believe that it is also true that there were issues with non-ext2 /boot partitions with earlier kernels, since ext2 is the only file system which used to natively support hibernate/suspend-to-disk. I also believe that this issue is resolved in newer kernel versions, which begs the question...

Does anybody know if this actually speeds up the system? Or is this practice outdated and unnecessary?

Mike

---

### Post by wpshooter on 2007-07-11
do "/" = root , type ext3
do "/home"   , type ext3
do "/swap"    ,type swap

---

### Post by mbsullivan on 2007-07-18
The question isn't to find a configuration that will work... ext3 is a great file system and will certainly work fine.  The question is whether there is any significant speedup from making a separate (ext2) /boot partition, as many have claimed.

I've never seen any actual benchmarks, and I'm skeptical that the issue is relevant, still.

Mike

---

### Post by kerry_s on 2007-07-18
it's moot, boot is loaded on ramdisk which is ext2 anyways, but ext2 can be read faster, but than again with the right settings(noatime,etc...) the other file types can be just as fast. I run my whole system on ext2, i've played with the others, but have noticed after a while they tend to slow down, perhaps it's just my perception, who knows. I just prefer ext2. :)

---

