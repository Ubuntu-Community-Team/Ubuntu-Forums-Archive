---
title: "error after upgrading to 10.4 and LTSP"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by deathscroll on 2010-05-18
Hi all,
 
after i've upgraded to 10.4 and after i've upgraded LTSP the system gives me the following error:
 
mount : mounting non on /dev failed: no such device
udevd [883]: error getting socket : Invalid argument
 
error initializing netlink socket
udevd [883] : error initializing netlink socket
 
libudev : udev_monitor_new_from_netlink : error getting socket : Invalid argument
 
Segmentation fault
 
Gave up waiting for root device - Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay = (did the system wait long enough?)
  - Check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules ; ls /dev)
 
ALERT! /dev/disk/by-uuid-e2b15003-2C90-4d32-89cd-46686C41758b does not exist. Dropping to a shell!
 
 
 
Is there someone who knows what I should do? 
 
If someone knows a answer in a hour I would be very grateful.

---

### Post by MikeUK on 2010-06-08
I don't know if it helps
But when I upgraded from 8.04 to 10.04 the upgrade allocated an incorrect UUID to the drive
a quick check with BLKID showed up the correct ID and an edit of the GRUB menu.lst solved the problem

---

### Post by MikeUK on 2010-06-10
Wrong thread

---

