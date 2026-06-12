---
title: "Partitions on hybrid SSHD hard drive..."
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by Z80A on 2016-10-09
I am about to install Ubuntu on a machine with a 1 Tbytes SSHD (hybrid 8 Gbytes FLASH and 1 Tbytes HDD) and I assume I just replicate what usually do:

1. **Boot** partition 512 Mbytes, ext 2 - /boot
2. **Root** partition 25-50 Gbytes - /
3. **Swap** - swap
4. **Home** - /home

Or any alternative ideas? I guess enabling **Host-optimized mode** would make a difference for /root and maybe swap:

[https://en.wikipedia.org/wiki/Hybrid_drive#SSHD_products_operate_in_two_primary_modes](https://en.wikipedia.org/wiki/Hybrid_drive#SSHD_products_operate_in_two_primary_modes)

Can this be done in Ubuntu 16.04?

---

### Post by frostschutz on 2016-10-09
Never heard of host optimized support before and no clue what it would look like and whether it would actually help.

Partition it normally. Make sure the partitions are MiB-aligned (which they should be by default when using any modern partitioner).

---

### Post by Z80A on 2016-10-09
This SSHD behavior may already be implemented in recent kernel versions, but I am struggling deciphering such information:

[http://lkml.iu.edu/hypermail/linux/kernel/1410.3/04551.html](http://lkml.iu.edu/hypermail/linux/kernel/1410.3/04551.html)

---

### Post by frostschutz on 2016-10-09
It's not in 4.7.6 ... at least not in the form you linked to.

> IOPRIO_ADV_EVICT, /* actively discard cached data */

```

~ $ cd /usr/src/linux-4.7.6
/usr/src/linux-4.7.6 $ grep -Einr IOPRIO_ADV_EVICT . || echo nope
nope

```

linux/Documentation/block/ioprio.txt only talks about helping CFQ scheduler to prioritize things, nothing at all about SSHD.

I don't think there is much chance of such features to be added either. SSHD never took off - way too expensive for negligible SSD portion, which will become useless once the mechanical side dies... and I don't see any new models coming out.

You might have more luck with dedicated SSD + HDD and software caching solutions like lvmcache.

Just use it like you would a regular hard disk.

---

### Post by Z80A on 2016-10-09
You are likely right on this - I will just treat is a normal 1 Tbytes drive and hope for some added speed.

I do realize that in a long term perspective the SSHD freak creature is somewhat of a Dodo - an evolutionary branch that will die out as more superior species (SSD) take over world domination. But right now, you can get some very good deals.

A friend of mine also pointed out that a benefit from the mechanical part of such a hybrid drive, is that the device will give out plenty of warnings (S.M.A.R.T.) before dying off. And this should not be the case with modern SSD devices which will work perfectly ...and the be gone. Now, I have no experience with this, so i may just be FUD from harddisk dealers with plenty of 320 Gbytes drive in stock. ;)

---

