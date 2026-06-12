---
title: "Partition scheme with sizes and question about upgrading"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by ioannis on 2006-09-10
I am planning on getting rid of Windows from my dual-boot windows + dapper machine. Since my dapper partition scheme is just one big partition for / and another for swap, I thought about going ahead and deleting everything and starting from scratch with a better partitioning scheme. After doing some searching on the forum, I know probably the best is creating partitions for /, home and swap, but I also saw suggestions to create separate partitions for /var, /tmp and some others. My questions are:

1. I was wondering if somebody could comment on the need for these extra partitions. 

2. In addition, my hard disk is 200 GB, how much should I assign to each partition? Is 1 or 2 GB for swap, X for / and the rest for /home the way to go? How much should X be?

3. After I create a /home partition and have a backup of it, if I upgrade to edgy and later releases, is anything on /home changed by the upgrade? If I restore /home from my backup after upgrading, will I be deleting upgraded things?

Thanks for the advice!

---

### Post by taurus on 2006-09-10
Personally, I would do something like

/dev/hda1 -> /boot (100MB)
/dev/hda2 -> / (50GB)
/dev/hda5 -> swap (1GB)
/dev/hda6 -> /home (whatever left...)

---

### Post by ioannis on 2006-09-10
> **taurus said:**
> Personally, I would do something like

/dev/hda1 -> /boot (100MB)
/dev/hda2 -> / (50GB)
/dev/hda5 -> swap (1GB)
/dev/hda6 -> /home (whatever left...)

Thanks for the advice. Is swap and home in an extended partition, or should I create all primary partitions?

---

### Post by taurus on 2006-09-10
Either way, doesn't really matter...

/dev/hda1 -> /boot
/dev/hda2 -> /
/dev/hda3 -> swap
/dev/hda4 -> /home

However, if you want to resize /home later to create another partition, then you are in deep trouble with the one above since you can only have four primary partitions.  Always think ahead and take the neccesary steps...

---

