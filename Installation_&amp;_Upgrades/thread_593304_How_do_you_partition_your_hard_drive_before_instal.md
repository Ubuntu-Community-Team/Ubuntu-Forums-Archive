---
title: "How do you partition your hard drive before installing Ubuntu?"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Uboontu on 2007-10-27
Here is how I partitioned my hard drive (250GB):

XP     60GB
/        60GB
swap  4GB
/home 78GB
/usr     10GB
/var     10GB
/tmp    10GB

Any suggestions?

---

### Post by forestpixie on 2007-10-27
I just have 3 - /, /home and swap. But I have another drive which is data. Swap is 1Gb, / is 8Gb the rest is /home.

I wonder why you need to split /usr etc away - what' going to happen if they fill up? Are you going to use 4Gb of swap.

---

### Post by paulkater on 2007-10-27
10Gb for /var is a bit wild, I'd say. I have (on Mandriva, sorry) a 4Gb /var partition of which 820Mb is used.

4Gb swap is a lot also, set that up equal to the amount of RAM you have in the machine. With 4Gb of RAM you should not have to worry about swap, really, unless you do a lot of image/video processing...

---

### Post by Uboontu on 2007-10-27
I listened to the Linux Reality podcast. In one of the episodes the person said he would partition his hard drive to have /, swap, /home, /usr, /var, and /tmp, because /usr, /var, and /tmp can be filled up in case that a program goes crazy. Putting them on separate partitions will prevent that from happening.

---

### Post by PmDematagoda on 2007-10-27
That is a very strange thing to say.

I just have a / partition on my Ubuntu system, it ensures that space for each part(/, home, var, etc.) does not run out unless space in the entire HD does.

---

### Post by plafuro on 2007-11-02
How important is swap nowadays anyway? I have 2GBs of ram and was wondering if i could get rid of that extra primary partition...

---

### Post by zekica on 2007-11-02
offtopic: Swap doesn't have to be a primary partition. I have my swap partition as a logical drive in extended partition.

---

