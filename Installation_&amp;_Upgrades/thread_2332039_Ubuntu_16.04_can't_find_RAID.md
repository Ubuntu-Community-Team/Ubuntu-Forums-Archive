---
title: "Ubuntu 16.04 can't find RAID"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by quizzicus on 2016-07-27
Greetings,

I just upgraded from Ubuntu 15.10 to 16.04, and it drops me into BusyBox with the following error:

Gave up waiting on root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/isw_dbaibaaaac_RAID5_2 does not exist.  Dropping to a shell!

Here's what I know so far:
[LIST=1]
[*]The boot args have not changed from what they were for 15.10 (root=/dev/mapper/isw_dbaibaaaac_RAID5_2 libata.ignore_hpa=0 ro)
[*]rootdelay=90 only causes a longer delay before the same failure.
[*]/proc/modules includes dm_raid, raid456, async_memcpy, async_pq, async_xor, async_tx, and libcrc32c
[*]The only item in /dev/mapper is 'control'
[*]The system will still successfully load if I select a prior kernel (4.2.0-42-generic) in grub. However, I'd like to use the 16.04 kernel (4.4.0-31-generic) if possible.
[/LIST]

Thanks,
John

---

