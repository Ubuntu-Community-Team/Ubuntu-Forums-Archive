---
title: "Help with buying new laptop and want to use my current hard drive?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by ontherooftop on 2010-12-03
Hi I am planning on buying a better laptop with higher processing power,
higher better and different graphic card but just wanna keep my current 250
gig hard drive with everything in Ubuntu working fine and compiz with everything set up. Would it be ok to change the hard drive with my current Set up to the new cpu? Would extra drivers also be detected?

---

### Post by efflandt on 2010-12-03
If you are using proprietary video drivers it would be best to revert to default video drivers before switching the drive to the other computer.  Other than that, a regular install on USB hard drive can boot on different computer with different hardware, so it should be easy enough to move a drive to a different computer as long as grub and your /etc/fstab use UUID's to identify partitions.

When I first got an SSD, I used my laptop to install maverick to it, and the drive worked fine when moved to my desktop.  It made me realize how slow my 4200 RPM laptop drive was (about the same as USB 2.0).  But I was booting Ubuntu from a USB hard drive from my desktop for a while before installing it internally, so if your older laptop has a slower drive than the new laptop, you may not even notice it if you are used to it.

Many computers no longer come with system disks, so the first thing you should do with a new computer before tampering with it is use the utility on the computer to create recovery disks and/or back up the system.

---

### Post by C.S.Cameron on 2010-12-03
You can clone your old HDD to your new HDD using dd.
Hook up your old HDD with a SATA to USB adaptor and boot the Live CD.
```
dd if=/dev/sdb of=/dev/sda
```
You will not be able to tell the difference.
However first confirm that sda is the new drive and sdb is the old one.
If the new drive is larger than 250GB you can expand the partition with gparted.
Why start off your new computer with an old hard drive.

---

