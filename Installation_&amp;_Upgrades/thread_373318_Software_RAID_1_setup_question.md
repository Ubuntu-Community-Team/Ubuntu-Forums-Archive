---
title: "Software RAID 1 setup question"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by mkuutti on 2007-03-01
I got myself a new silent workstation and decided to convert my old workstation as backup/file-server. I found two PATA drives, one 100GB WD and 40GB seagate. My idea was to setup server where I could from time to time backup stuff from my new workstation. I quickly calculated that if I setup 59GB root partition and 1GB swap on 100GB disk, I can create 40GB RAID-1 partition to secure my data.

Ok, that's what i did, installed Edgy from alternate cd and created such partitions and md-device from /dev/hda2 and /dev/hdc1. System works great, but now realized that I have my system on 100GB(lots of hours behind) disk which is most likely to break before that 40gb disk. How do I recover? 

If my 40GB drive fails, I'll get new one and create 40GB partition and do that mdadm macig. But if my system disk fails, I'll get replacement drive and install new system... Should I create raid volume during installation, doesn't that delete my data? Or should I just leave empty 40GB partition and try to create new md manually? 

md-device is in fstab in UUID-format:
```
UID=df8fc280-fcb1-4b8b-8238-96c32b7d2bb3 /srv reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid,acl 0 2
```
and /etc/mdadm/mdadm.conf contains:
```
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e319fefd:93042527:a57be193:4b8f8544
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e319fefd:93042527:a57be193:4b8f8544
```
and my disk setup:
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7173    57617091   83  Linux
/dev/hda2            7174       12036    39062047+  fd  Linux raid autodetect
/dev/hda3           12037       12161     1004062+  82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4863    39062016   fd  Linux raid autodetect
```

So my question is: what should I backup to bring back my system in case of systemdisk fails OR should I just forget RAID-setup and trust that both computers won't fail simultaneously?

I feel like a newbie :confused:

---

