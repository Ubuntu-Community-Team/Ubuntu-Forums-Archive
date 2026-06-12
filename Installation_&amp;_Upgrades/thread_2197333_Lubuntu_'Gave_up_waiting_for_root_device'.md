---
title: "Lubuntu: 'Gave up waiting for root device'"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by burappinoitoko on 2014-01-03
Hello.

I'm a new Linux user and have an old Acer Apsire PC with Windows 7 with a Celeron processor that is too slow to really be useful. I decided to try Lubuntu on it, and when I run it off of the live disc, everything is flying.

When I intalled Lubuntu however, I get the following error message when I try to boot:[INDENT]
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ed664156-5e45-4c1e-ae16-d03be8009faa does not exist.
Dropping to a shell![/INDENT]

Any idea what I can do? I checked the disc for defects, and found nothing wrong, and it works great when running it from a live CD. I tried using bootloader, but couldn't get i to work.

The version I'm trying to install is 13.10.

---

### Post by ubfan1 on 2014-01-03
When running the live session, run sudo blkid and see if the uuid is correct on the root (/) filesystem (it probably is).  If that's OK, then take a look at the <wherever the  hard disk is mounted in the live session>/boot/grub/grub.cfg file, and see what devices are used for things like set root = (hd0,msdos?)  That should be hd0 for the hard disk with no other usb disks inserted, if it's hd1 (or anything else), edit them back to hd0.  Any explicit devices like /dev/sdb? should also be changed to /dev/sda?  then try to boot again off the hard disk.  at the first successful boot, run sudo update-grub just to make sure everything is fixed permanently.  You could try the rootdelay=10, but I've never actually had to use that.  Sorry I forget where the hard disk gets mounted, in the live session.  Maybe you have to mount it yourself at /mnt.

---

### Post by Quackers on 2014-01-03
Does the system boot if you leave that display for a few moments and then press enter?
It could be that your hard drive is not spinning up fast enough for the system. Adding the boot argument rootdelay=30 might help.

---

