---
title: "Server install on RAID 1 / cryptsetup"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by jkounis on 2013-02-01
My current server is running 10.04 on an encrypted hard drive, which I installed with the Ubuntu Alternate install CD a few years ago. It has been running flawlessly, so I'm familiar with encrypted hard drives.

I just tried to use the 12.10 server install cd to set up a server on an encrypted raid 1 array. The steps are:

[LIST=1]
[*]Partition two hard drives with two partitions each.
[*]Set up a raid 1 array on /dev/sda1 and /dev/sdb1
[*]Set up another (small) raid 1 array on dev/sda2 and /dev/sdb2
[*]create an encrypted volume on the first raid array
[*]set up the second raid array to contain /boot
[*]partition the first raid array into three partitions for /, swap, and /home
[/LIST]

The installation seems to work fine. However, when I boot the system, it tries to unlock the disk and absolutely will not accept my password. I have tried to install from scratch twice, and both times it acts as if the password I type when I first boot the system is incorrect.

Is there a problem installing a server on top of a RAID 1 array?

---

