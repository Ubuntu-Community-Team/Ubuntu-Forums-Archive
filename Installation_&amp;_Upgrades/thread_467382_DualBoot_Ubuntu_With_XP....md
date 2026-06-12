---
title: "DualBoot Ubuntu With XP..."
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by lionknig93 on 2007-06-07
Hello...

I currently have a Microsoft Windows XP Pro., and would like to dualboot it with Ubuntu.

I already have the LiveCD, and I have tried to install it, everything seemed fine until the partitioning step apeared, I currently have 80 GB HDD, and used 50 GB to the Windows XP. The 30 GB left are not formated, they are just unpartitioned space.

I would like to know how to partition my HDD the right way, with a guided installation help.


Thanks.

---

### Post by merlinus on 2007-06-07
Defrag your windows drive several times first.

The guided partitioning will resize windows and use the free space to set up at least two partitions, / and swap.  The latter should be about 1.5 times your RAM.

You might also consider creating a separate partition for /home.

So you can allocate about 20G to / and 10G to /home.

-merlin

---

### Post by Phulpreet on 2007-06-13
Heyy, i have tired using the guided partitioning but it does not seem to work, i have a 120 GB hard drive, and the whole thing is partitioned to XP, how can i partition about 30gb and then install Ubuntu?

---

### Post by merlinus on 2007-06-13
When you say that the Guided partitioning did not work, can you be more exact?

You need to re-size your windows partition to free up the space for ubuntu.

Perhaps the Manual option will work better.

If none of these work, then the gparted live cd will do the job:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

