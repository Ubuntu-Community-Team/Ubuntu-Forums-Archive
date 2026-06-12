---
title: "Fail to mount sda1 after 10.04 install"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Kungfujon on 2010-05-03
After upgrading from 9.10 to 10.04, Ubuntu now tells me that it can not find "sda1" to mount.

This computer was originally a windows machine.  Then I installed Linux and created a dual boot with separate partitions (windows = sda1 and Linux = sda2).  After getting comfortable with Linux, I deleted my Windows partition (and expanded the linux partition to fill) and now run a pure Linux machine.

My thought is that "sda1" is the old windows partition that it is looking for.  I used gparted to review the partitions, and this is what I have:

sda2 = "ext3" 92 GiB
sda3 = "extended" 1.42 GiB
-sda5 = "linux swap" 1.42 GiB
sda4 = "unknown" 203.95 MiB

So, is there anyway to rename my "sda2" to "sda1" without wrecking my install?  Or is there a way to get bootup to stop looking for it?

and...do I need to do anything about that "sda4"?

Thanks for any help you can offer.

Jon

---

