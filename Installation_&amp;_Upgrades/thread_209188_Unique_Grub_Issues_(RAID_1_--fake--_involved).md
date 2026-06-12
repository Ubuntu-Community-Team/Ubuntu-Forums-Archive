---
title: "Unique Grub Issues (RAID 1 --fake-- involved)"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by truantology on 2006-07-04
Hey all,

I have a rather unique problem...let me give you some background:

when I decided to install dapper, I wanted to utilize my sata drives (2 identical 300 gigs) as a Raid1 array.

I had been messing around with M$ vista-b2, so I had a 120gb PATA drive installed as well.  

I set up a software raid1 array using [this guide](http://users.piuha.net/martti/comp/ubuntu/raid.html) as a base, and everything installed fine, but when it installed grub, it installed it on the MBR of /dev/hda...which of course is my PATA drive.

**_The Problem_**
I don't use vista-b2 anymore, and the PATA drive isn't being used for anything...additionally, it's causing a lot of unwanted heat in my box.  I want to physically remove it from the box, but if I do that, it won't boot due to lack of grub on the MBR.

How do i install grub on my SATA drives so that when i remove the PATA hard drive, the computer still boots   properly?

Thanks,
TruANT





*Output of "sudo fdisk -l"*
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  fd  Linux raid autodetect
/dev/sda2   *         123       19520   155814435   fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  fd  Linux raid autodetect
/dev/sdb2   *         123       19520   155814435   fd  Linux raid autodetect

Disk /dev/md0: 1003 MB, 1003356160 bytes
2 heads, 4 sectors/track, 244960 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 159.5 GB, 159553880064 bytes
2 heads, 4 sectors/track, 38953584 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

```

---

