---
title: "Different filesystem for different partition"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by meson2439 on 2011-01-21
Is it advisable to use different filesystem for different partitions?
For example: 

I plan on using ext4 or JFS for / however on /home I would prefer to use XFS.

Will such setup cause performance penalties?

I've used both ext4 and XFS. XFS is extremely faster when handling transfers but ext4 has faster boot-up time and program startup. So I thought if I use separate filesystem, I will get the best of both worlds. I haven't got to try it yet (no spare pc at the moment) but I wonder if someone else got the experience.

Thanks in advance.

---

### Post by srs5694 on 2011-01-22
There's no problem with mixing your filesystems. I do it on many of my computers. In fact, most computers do it at least some of the time -- dual-boot configurations typically use at least two filesystems (at least one for each OS), and even single-boot computers use multiple filesystems when mounting CDs, DVDs, or often even USB flash drives, since these media typically don't use the filesystems that are common on hard disks.

The only performance penalty I'm aware of from using multiple filesystems is that doing so requires loading more drivers into memory. I just checked, and most filesystem kernel modules seem to be between 100KB and 700KB in size, so each new filesystem will consume roughly that much RAM. This will in turn cause the system to start swapping that much sooner. I doubt if you'd notice this effect in practice.

---

### Post by meson2439 on 2011-01-23
Thanks. Your explanation is informative.

---

