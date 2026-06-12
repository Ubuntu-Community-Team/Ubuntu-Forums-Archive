---
title: "dmraid, FastTrak, can't see partitions"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by yHg2bFsM on 2007-08-22
Hello

I'm using Kubuntu Feisty 7.04.
I have a Promise FastTrak100 TX2 (PDC20270) RAID controller, two hard drives connected to it and I'm using RAID 0 (stripe). On this RAID there are 3 Windows partitions (NTFS).
I have Kubuntu installed on a separate hard drive not connected to the RAID controller.
Up until recently everthing was working, I was using dmraid and I could see the partitions on RAID as device files in /dev/mapper like so:

ls -1 /dev/mapper
control
pdc_bihediea
pdc_bihediea1
pdc_bihediea5
pdc_bihediea6

I would then mount the partitions as needed, I only need to copy a few things on occasion.


Then I moved my Kubuntu installation to another hard drive. I simply copied the files, there were a some minor problems but it worked out, except that now I can't see (and mount) the RAID partitions any more because I can't see them.

ls -1 /dev/mapper
control
pdc_bihediea

These are the only two things in /dev/mapper. If I open pdc_bihediea with cfdisk for example I can see the three partitions but I don't know how I can mount them.

Any suggestions?
Thanks

---

