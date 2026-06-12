---
title: "New software RAID array being detected as /dev/md0"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by cmokruhl on 2006-09-06
I've searched high and low but can't seem to find a similar issue...  A while back, I installed Breezy (server) on a software RAID1 array.  3 partitions:

/dev/md0 for /boot
/dev/md1 for swap
/dev/md2 for /

These were on 2-120GB PATA drives (/dev/hda and /dev/hdc) and all was well.  I recently upgraded to Dapper via apt-get and that went fine.  Yesterday, I got a new 4-port SATA controller card (Promise SATA300 TX4) and 4-320GB hard drives in the hopes of setting up a new software RAID5 array for data.  I ran:
```
mdadm --create --verbose **/dev/md3** --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```Everything went fine as far as creating the RAID array and it showed up correctly in /proc/mdstat as /dev/md3.

Here's the problem: after a reboot, the new RAID5 array gets detected as /dev/md0, shifting all the other arrays up one (md0->md1, md1->md2, md2->md3).  Obviously, that doesn't boot since the root is no longer on /dev/md2.

What can I do to stop the new RAID array from being autodetected as /dev/md0?  I've tried using fdisk to change the file system type from "Linux raid autodetect" to "Linux" on /dev/sd* in the hopes that it wouldn't be autodetected, but it still is.  I've tried forcing it in /etc/mdadm/mdadm.conf:
```
DEVICE /dev/hd* /dev/sd*
**ARRAY /dev/md3 level=raid5 num-devices=4 UUID=6bf82f9e:8baf6938:93ceff4c:e05fbde4**
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=22c3835e:cf313877:e282d0bd:8b2876f5
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=005c8921:8f4d2279:dcd2e81d:565e7f3e
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=988726d2:fdf2d742:494c3d23:53304988
```However, mdadm is loaded long after the autodetecting of RAID arrays.  I've also tried changing /etc/fstab and /boot/grub/menu.lst to use the "revised" /dev/md* numbers, but something crashes hard during boot.  My guess is it all has something to do with the kernel searching the SATA drives before the PATA drives, but the boot order is definitely correct in the BIOS since grub loads.  I can get everything back to normal by zeroing out the superblock on /dev/sd* or removing the SATA controller card.  Ideas?

---

