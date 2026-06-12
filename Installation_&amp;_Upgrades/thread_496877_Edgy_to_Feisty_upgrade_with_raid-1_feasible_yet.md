---
title: "Edgy to Feisty upgrade with raid-1 feasible yet?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Ben Branch on 2007-07-09
Hi!

I'm happily running Edgy with two SATA drives (/dev/sda and /dev/sdb). Each has three partitions
which are in RAID-1 (so I have /dev/md0, /dev/md1, and /dev/m2). All is working just fine. (This
is Linux software raid, no BIOS involved).

I'm a bit skittish about the automatic upgrade because I've seen so many reports about
RAID issues. Is the Feisty upgrade read to handle a pretty standard raid-1 upgrade yet?

I just upgraded my vanilla (single hdd) laptop to Feisty without any prob, but my desktop
holds the master of all my stuff ... don't need any headaches there ...

Thanks,
Ben

```
blb@tbroma: cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sda3[0] sdb3[1]
      87915648 blocks [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[1]
      1951808 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      7815488 blocks [2/2] [UU]
```

---

### Post by Ben Branch on 2007-08-04
OK, thought I would report. Did the upgrade a few days ago, and my RAID-0 from
edgy was still in good shape. (It did ask me during the upgrade if I wanted /dev/md0
to be formed early because root was on it. I said yes, of course).

There were other problems with the upgrade, but the RAID wasn't one of them.

---

