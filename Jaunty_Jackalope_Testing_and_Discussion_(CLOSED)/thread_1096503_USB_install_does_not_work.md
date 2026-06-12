---
title: "USB install does not work"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SickBeast on 2009-03-15
I tried installing Ubuntu 9.04 onto my 4gb USB flash drive, and it failed immediately when running from the bootable CD.  I tried it again from within the OS installed on my hard drive, and it failed, this time after having written 697mb to the USB drive itself.

As an aside, the installer won't let me use the EXT4 filesystem on the USB drive at at all.  It made me format to FAT32.  IMO EXT4 should be an option as it would probably be faster.

---

### Post by jerrylamos on 2009-03-15
Take a look at launchpad bug 331327:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/331327](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/331327)
As of alpha 6 there's a bug in the usb startup disk creator....

Jerry

p.s. lots of reports on Ext4 losing data....good luck.  By "tradition" the usb drives are used with fat 32 which among other things has more space than Ext3 etc.

---

### Post by jerrylamos on 2009-03-16
As of today's updates to a bunch of packages including the USB creator I was able to install onto a USB.  The USB did then boot and run.

However I wasn't able to do an install from the USB because the partition frame didn't have any partitions in it.

When I tried to shut down the USB, there was an error; could have been flash error, I don't know.

Partial success, anyway.

Jerry

---

### Post by whoop on 2009-03-16
Just a few minutes ago I created a usb startup disk using jaunty. It booted successfully and I used it to convert my ext3 partition to ext4. It also "shat down" ;-) correctly..

I did not do a install with it though.

---

