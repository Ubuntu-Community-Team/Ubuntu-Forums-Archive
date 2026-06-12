---
title: "how to partition server, seek advice"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by gian on 2007-10-15
hello All,

I am doing some tests on a tower pc with 4 scsi disks under an Adaptec RAID card set up as RAID 10 (two RAID 1 combined) for a total capacity of 35GB.

When I launch the 7.04 alternate installer, I only see one disk, and I plan to partition as follow:
/ 8GB ext3 primary beginning
/home 16GB ext3 primary beginning
/office 8GB ext3 primary beginning
/swap 1GB logical
2GB unused space

Does this make sense? I'm not talking about sizes, I'll have plenty of space on the production server.

LVM, I would do without it. What am I loosing? If I need to enlarge one partition, I should be able to do it with parted, correct? I admit that my decision comes from the fact that I did not really understand how LVM has to be setup, no matter how many times I tried, and anyway, with hardware RAID Ubuntu sees only ONE disk, and not the single units.

thanks for your time,
-Gian

---

