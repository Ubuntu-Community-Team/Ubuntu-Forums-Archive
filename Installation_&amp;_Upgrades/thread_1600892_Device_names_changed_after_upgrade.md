---
title: "Device names changed after upgrade"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by pwlodarczak on 2010-10-19
Hi there,
After upgrading from 10.04 AMD 64 to meerkat the device names changed. Eg my device with the boot partition is now called /dev/sdb and it used to be /dev/sdd. This is very annoying since I had to change all mount points in fstab. Can I change the device names back to what it used to be?
Thank you
Peter

---

### Post by Morimando on 2010-10-20
Quite annoying, yes. Here it changes drive names too... sdb1 is sdf1 every other boot...
I've not yet looked into this very much, I guess you can still write udev rules for the drives and assign the name you want. 
For the moment, I changed fstab's contents to contain the UUID of the partitions rather than their kernel names. To avoid doubles in Nautilus, I called them /dev/disk/by-uuid/UUID. Here's an example:

```
/dev/disk/by-uuid/e339ee09-6633-4b18-98d4-af0dccbc31c6 /media/Multimedia btrfs user 0 2
```

You can find the UUIDs by issuing the command:
```
ls -l /dev/disks/by-uuid
```

---

### Post by pwlodarczak on 2010-10-20
That worked, thanx a lot. Just a minor correction, the command is:

```
ls -l /dev/disk/by-uuid
```

---

