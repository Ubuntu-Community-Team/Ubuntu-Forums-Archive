---
title: "mdadm kills sata?"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by m0rtal on 2008-01-20
I've lost whole weekend trying to make mdadm work correctly.
I had a working gentoo server with 3xSATA and software RAID5 running on it.
Then I've decided to move to ubuntu, and I didn't want to lost data from that raid.
Installation went smooth, I've installed mdadm, ran "mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1", and voila - raid is up, tried to mount - no problem, files are here.
BUT!
When I rebooted, I lost raid!
cat /proc/mdstat says:
> Personalities: [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10
md0: active raid5 sdb[1] sdc[2]
781422592 blocks level 5, chunk, algorithm 2 [3/2] [_UU]
unused devices: <none>
As you can see, mdadm here works with sdb and adc instead of sdb1 and sdc1, not mentioning about missing sda1. And here comes the funniest part - /dev/sd* is gone!
What's wrong?
I've already totally reinstalled Ubuntu - just in case, you know... and ran into same strangeness.
What am I doing wrong?

---

### Post by m0rtal on 2008-01-22
any ideas?
I can't access any of th sata disks, and that's really frustrating :(

---

