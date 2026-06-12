---
title: "Upgrade 10.04 to 12.04--will not boot-drive not ready message"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by prospero52 on 2012-09-29
Ok, I guess I need help with this.  I have a dual boot Vista/Ubuntu HP system.  I decided to finally upgrade my 10.04 LTS to 12.04.  All seemed to go well, but when I attempt a reboot, I get this message:  "The disk drive for / is not ready yet or not present".  Hit 'skip' and it then says "The disk drive to /tmp is not ready or not present".  Try another 'skip" then its: "the disk drive for /mnt/sda1 is not ready or not present."  It hangs thereafter.  If I go to manual recovery and type "fdisk -ls", all partitions for sda1 are listed and are correct. Vista boots normally (not that I use it much!)  Not a newbie at Ubuntu, but certainly not fluent.  Any info/help would be much appreciated.

---

### Post by prospero52 on 2012-09-30
A bit more info may help.  This error occurs about halfway through the boot process.  If I go into manual recovery, the system tell me that "Root filesystem check failed".  It is almost as if it is looking for the filesystyem on the wrong partition, as it fails looking on sda1, which is the Vista partition, not sda2 where ubuntu resides.  Any ideas how to correct this?  Would hate to have to do a full reinstall.

---

### Post by bart.a on 2012-10-18
Maybe you can do a live cd recovery..
I would suggest downloading the iso again and check it's integrity before burning it and checking it again..

Then use [this link]("http://help.ubuntu.com/community/LiveCdRecovery") to re-update/re-upgrade your system..

Hope this works for you..

---

