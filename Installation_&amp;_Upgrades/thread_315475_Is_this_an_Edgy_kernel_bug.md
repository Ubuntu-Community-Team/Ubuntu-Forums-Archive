---
title: "Is this an Edgy kernel bug"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2006-12-09
After upgrading to edgy, occasionally my slave drives will become read-only.  I've wasted a lot of time on false leads and am about to reformat my root partition and reinstall 6.06, which I would consider a moral defeat.  So I am asking this in desparation.


The relevant line in my fstab is (currently)

/dev/sda1        /data_disk1  ext3    defaults      0 0

although I also get this behavior when I have the UUID.

It just happened again.  Usually if I reboot the problem goes away for a few days.

This time I decided to unmount the partition.

When I try to remount, I get this:

```

% sudo mount -t ext3  /dev/sda1  /data_disk1 
mount: /dev/sda1 is not a valid block device

```

I've tried every other conceivable version of this command.

Normally, a simple

sudo mount /data_disk1

does the trick. The error is specifically associated with the glitch where the disk becomes read-only.

Worse, if I don't reboot, the disease spreads.  Eventually it effects even the root partition.

This is driving me nuts and has been the single most protracted bad experience I have had with Ubuntu by a factor of 10.

---

