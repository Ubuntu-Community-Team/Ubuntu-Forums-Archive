---
title: "Mounting RAID in 12.4"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by Mad-One on 2012-10-07
Hi,

I' still trying to mount my RAID array after upgrading to Pangolin. The array assembles OK but on trying to mount it I get the following:

> MO@Linux-U2:~$ sudo mount -a -t auto /dev/md0 /mnt/RAID
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?It's obviously not NTFS but I'm not sure what format type I should use and I can't reformat as I have data on the array.

TIA - MO

---

### Post by darkod on 2012-10-07
You are not sure what filesystem you have on your raid?

The first thing is whether the array gets assembled automatically on boot, or you have to do it manually. If it's done auto, no problem.

Then you can check the filesystems with something like:
sudo parted -l (small L)

If there is no entry for the raid in /etc/fstab and you want it to mount on every boot, you will need to create an entry in /etc/fstab.

---

