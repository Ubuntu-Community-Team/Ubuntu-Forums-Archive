---
title: "Growing Raid5 Array Issue"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by djh82uk on 2010-12-27
Hi Guys

I am running Ubuntu server 10.04.  I have a single drive that runs the OS (sdf1) and a raid 5 array (md0).  It currently consists of 4 x 1.5TB drives.  It is full so I am having to install another 1.5tb drive.

I cannot back it up as it is just too much data. and I think I made a mistake.

I installed the drive physically and then ran: mdadm --add /dev/md0 /dev/sde followed by mdadm --grow /dev/md0 --raid-devices=5

No errors all looking good, but then I noticed that all the drives in the array are sda1, sdb1 etc, but the drive I added was sde without a 1 on the end "sde1 does not exist".  Is thos because sde was not formated? (I thought mdadm would do it).  And if so what effect will this have once the reshape finishes? (currently on 1.3%)

Do I have a problem?  And what can I do?

Thanks

DJH

---

