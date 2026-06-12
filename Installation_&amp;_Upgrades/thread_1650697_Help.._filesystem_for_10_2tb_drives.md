---
title: "Help.. filesystem for 10 2tb drives?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by c2h2 on 2010-12-22
What would you recommend the best files system to use for a low-cost web photo storage server online? I have got 10 x  WD 2TB (EARS) drives.

Ubuntu OS will on a OCZ SSD. and leave these drives in a group. Preferably the group could provide:
* fast random read performance
* reliability
* redundancy
* easier disaster recover 

Should I go for?
1. hardware RAID adapter, for RAID5/6? 
2. software raid / LVM ? 
3. fuse ZFS?
4. JBOD EXT4?
other alternative?

---

### Post by srs5694 on 2010-12-23
You'll definitely need some form of RAID. I'd use either a true hardware RAID adapter or Linux's software RAID, not the motherboard/Windows version of software RAID (sometimes called "fake RAID").

You might want to look into using LVM atop RAID. (See [here,](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) among many possible sources, for more LVM information.)

I wouldn't recommend ZFS for a Linux system, since ZFS is not supported natively by the kernel; it's only handled via FUSE, which is likely to degrade its performance and reduce its reliability. XFS is a native Linux filesystem that can do what you need and has a good reputation; use it. (OTOH, I've not seen any actual benchmarks comparing ZFS to XFS under Linux. Perhaps the results would surprise me.) In principle, ext4 should work fine; however, the current utilities to create ext4 filesystems max out at something much lower than ext4's limits (2 TiB, IIRC; but maybe I'm not remembering correctly). New utilities will eventually raise these limits, but I don't recall if they're available yet. Eventually Btrfs will be a good choice, but I wouldn't recommend it for anything mission-critical at the moment; it's too new and is considered experimental.

---

### Post by c2h2 on 2011-01-11
thanks, i will give LVM a go

---

