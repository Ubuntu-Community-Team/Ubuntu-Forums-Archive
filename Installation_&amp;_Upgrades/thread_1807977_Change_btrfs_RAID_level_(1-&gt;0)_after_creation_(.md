---
title: "Change btrfs RAID level (1-&gt;0) after creation? (for metadata only)"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Interruptor on 2011-07-19
I have installed Natty on the btrfs and then added second disk to create RAID0. The problem is that the Metadata was put in RAID1:
> $ sudo btrfs fi show
Label: none  uuid: 52e...b174
	Total devices 2 FS bytes used 6.42GB
	devid    1 size 3.76GB used 3.47GB path /dev/sda1
	devid    2 size 15.03GB used 8.97GB path /dev/sdb

Btrfs Btrfs v0.19

> $ sudo btrfs fi df /
Data, RAID0: total=5.17GB, used=1.90GB
Data: total=5.00GB, used=4.25GB
System, RAID1: total=8.00MB, used=4.00KB
System: total=4.00MB, used=0.00
Metadata, RAID1: total=896.56MB, used=263.33MB
Metadata, DUP: total=256.00MB, used=15.72MB
(this is Asus Eee PC 901 with two SSDs).

Is there a way to tweak it and switch from RAID1 to RAID0?

---

