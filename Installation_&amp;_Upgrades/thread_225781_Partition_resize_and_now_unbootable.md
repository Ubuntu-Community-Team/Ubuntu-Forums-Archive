---
title: "Partition resize and now unbootable"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Lunar_Lamp on 2006-07-30
A rather lengthy explanation is required here, so please bear with me.

I had 20gb of unallocated space on my hard drive, and to cut a long story short, I decided to use partimage to backup my / and /home partitions to usb disk, delete them, recreate them to use the available space, and restore tehm using partimage.

I should note that in the process my /home partion and /root partition switched around (i.e. /dev/hda3 was / and is now /home and vice versa).  I edited my /etc/fstab to reflect this.

After doign this I got a grub error 15, so fixed my MBR according to this section here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857)

I can now boot into windows, but my ubuntu installation will not boot.

The error message I get is this:

```
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 [snip]

/bin/sh: can't access tty; job control turned off
```

---

### Post by Lunar_Lamp on 2006-07-30
I realised that I hadn't fully edited my grub menu.lst file.  Oops!

---

