---
title: "attempting to rescue ReisferFS drives"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by 4heid on 2008-10-09
I have an Asus WL700ge router with built in HD that was using ReiserFS. Attached to it was a USB HD which through the router software was formated Reiserfs and acted as a software Raid1 mirror.

The router itself has failed and I am trying to mount either of my drives, the base unit or the mirror to Ubuntu.
They are seen as SCSI drives for some odd reason and wont mount.

Heres what I have accomplished:
installed asus hd in ubuntu box as slave, it reads as:
-------------------------------------------------
Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
-------------------------------------------------

fdisk /dev/sdb says Unable to open??

when I tried fdisk/dev/sdb it says "Permission Denied", this I couldnt get past the first step of making a backup of the first 512 bytes.

I also have a USB drive that was acting as a raid mirror.

When attempted each drive type and letter it just says, Unable to Open.

Any thoughts?

TIA,
Chris

---

### Post by 4heid on 2008-10-11
bump...

still cant access these drives, anyone have any thoughts on why they are not mountable?

---

### Post by 4heid on 2008-10-11
ok, finally was able to get somewhere in ubuntu but now it says as i was trying to mount it,

mount - you must specify file system type. 


its currently reiserfs, how do i specify this and not lose the data on the hd?

---

### Post by cariboo on 2008-10-11
Have you tried:

```
mount -t rieserfs /dev/sdxx /mnt
```

You title sounds like trying to break Hans Rieser out of jail :)

Jim

---

### Post by Sef on 2008-10-11
> You title sounds like trying to break Hans Rieser out of jail :smile:

For those who don't get the joke:  Hans Rieser pled guilty earlier to killing his wife.

---

