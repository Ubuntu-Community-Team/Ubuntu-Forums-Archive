---
title: "After successfully installing 14.04 from a usb I find that my usb is no longer usable"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by squirebug on 2015-01-22
After successfully installing 14.04 from a usb I find that my usb is no longer usable.  All the file permissions have been set to read only and windows does not recognize it.  Can I ever use my usb again?  If so, how?

---

### Post by sudodus on 2015-01-23
Please do not hijack threads! I moved your post to an own thread with what I hope is a good title. I can change the title if you wish.

-o-

How did you make the USB pendrive bootable, which tool did you use?

One way to try to restore a pendrive is to wipe the first megabyte with ***mkusb***, and then create a new partition table with ***gparted***. If mkusb and gparted are not able to write to the pendrive, it is probably dead. Notice that you may have to unmount the partitions to allow gparted to do its job.

Device -- Create partition table ...

See [this link for more details]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

