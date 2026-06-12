---
title: "Migrate OS from HDD to USB Flash?"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by 13eastie on 2012-07-16
I have a HP Proliant Microserver N40L running 12.04 LTS Server.

I built the OS on the supplied 250 GB HDD prior to deploying a RAID1 array using mdadm.

It works perfectly, but I'd like like to free up a drive bay for further expansion and one option would be to migrate the OS onto a USB stick.

Can anyone tell me whether this is as straightforward as restoring a backup to the USB stick (with suitably-sized swap and ext2-formatted-bootable partitions) before restarting?

---

### Post by Cheesehead on 2012-07-16
Essentially, yes...but it will be *much slower* than you are used to. And the frequent R/W cycles (like writing events to log) will prematurely wear out the USB stick.

---

### Post by sudodus on 2012-07-16
> **Cheesehead said:**
> Essentially, yes...but it will be *much slower* than you are used to. And the frequent R/W cycles (like writing events to log) will prematurely wear out the USB stick.
+1
It is important to have rapid access to the operating system. If you need to move something out of the computer case, I think it is a better idea to move some of the stored data to an external drive. eSATA and USB 3 are much faster than USB 2.0.

---

