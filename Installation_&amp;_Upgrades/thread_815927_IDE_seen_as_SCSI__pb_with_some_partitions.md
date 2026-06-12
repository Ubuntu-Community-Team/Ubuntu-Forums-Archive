---
title: "IDE seen as SCSI : pb with some partitions"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by 6BerYeti on 2008-06-02
Dear All,

I am new heren, and quite new with Ubuntu.
I have been glad to install Gustsy Gibbon without any problem.
It was a trial, waiting for Hardy Heron (LTS).

I have only PATA/IDE drives. No SATA or SCSI
Hardy Heron seems to use a Linux kernel with the new unified driver for disk access.
As I have a lot of partition (too many perhaps ... but let's keep that for now on), 2 of my partitions are not correctly recognized : there were previously named hdb16 and hdb17.
They should now been named sdb16 and sdb17.
In fact, gparted sees them as sdb16 and sdb17, but cannot access to. In fact, neither /dev/sdb16 nor /dev/sdb17 is created. And it seems impossible to create and use it.

Is there a simple workaround for such a situation, where a drive has many partition and you want to migrate to Hardy Heron.

Thanks for your help.

---

