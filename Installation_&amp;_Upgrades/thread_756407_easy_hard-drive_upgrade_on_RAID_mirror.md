---
title: "easy hard-drive upgrade on RAID mirror?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-04-15
I'm currently running my main production workstation on Ubuntu 7.04 with two identical 160 GB SATA drives setup as a RAID mirror.  Everything works great.  I want to upgrade to 7.10, and then 8.04, and I also want to replace my drives with a pair of new 320 GB.

I've been playing around with a test system and it **seems** like it's a lot easier than any of the How To guides I've been able to find describe it.  For instance, here are a few previous guides:
[LIST]
[*][http://mkfblog.blogspot.com/2007/11/resizing-raid1-system-partition.html](http://mkfblog.blogspot.com/2007/11/resizing-raid1-system-partition.html)
[*][http://www.debian-administration.org/articles/424](http://www.debian-administration.org/articles/424) [/LIST]
_________________________

Now, here's my proposed technique:

**PREPARATION**
[LIST]
[*]update boot scripts to support 1-drive booting; install GRUB on #2 drive
[*]check that each drive can boot individually
[*]remove original drive #1; keep as fall-back
[*]install replacement drive #1[/LIST]

**UPGRADE DRIVE #1**
[LIST]
[*]boot from drive #2; the array(s) will be in 'degraded' mode
[*]use GPartEd to create 'unformatted' partitions for how you want everything to end-up.
  (They don't need to match the originals, they just need to be equal or bigger.)
[*]use Manage Flags option to mark the partitions as 'RAID'
  (Also add 'Boot' for the root partition)
[*]add the partitions back into the array, e.g.
```

 > sudo mdadm --add /dev/md0 /dev/sda1 
```
[*]wait until the array has finished re-syncing, i.e., check the status,
```

 > cat /proc/mdstat 
```
[*]re-install GRUB on new drive #1[/LIST]

**UPGRADE DRIVE #2**
[LIST]
[*]repeat the same steps as before but remove/replace the original drive #2[/LIST]

**EXPAND THE ARRAY TO THE NEW SIZE**
[LIST]
[*]expand the array(s), e.g.[/LIST]
```

 > sudo mdadm --grow /dev/md0 --size=max 
```
**EXPAND THE PARTITION TO THE NEW SIZE**
[LIST]
[*]expand the partition(s) within the array(s), e.g.
```

 > sudo resize2fs /dev/md0 
```
[/LIST]
**NOTES**
[LIST]
[*]All these array/partition expansions can be done 'online' and without needing to boot a LiveCD or otherwise take the drives off-line.  (Obviously, you need to shutdown the computer when you swap the drives.)
[*]These steps are identical to the first reference link I included ("MKF Blog") except that I didn't need to do any of the steps from #11 on.  (Actually I may have had to go offline?  I honestly can't remember what all I did because I've wasted a lot of time trying to 'satisfy' Gparted; see below.)
[*]The expanded partition/arrays are "active" and "clean" according to mdadm.[/LIST]
The only problem I've found is that Gparted reports an error with my test array, which is on an Ubuntu 7.10 install, even before I do any upgrades!  I'm hoping that it's just because it's too old a version (v3.3).  But I sure would like to know for sure if my proposed technique is sound before messing with my production system.  Can anyone comment on it, e.g. point-out anything I've missed?  Thank you!

P.S.  I'm currently in the process of recreating my procedure from scratch, so I'll be able to confirm if the partition expansion really was do-able online.  And I'll also be prepared to do any additional testing or verification...

---

### Post by bsmith1051 on 2008-04-16
So I re-did all these steps on my test rig and it really did work online, without need to boot from CD or anything.  If it makes any difference, I did the 'resize2fs' command with only the first replacement drive in-place.  Maybe the version in Ubuntu Gutsy (v1.40.2) has new support for online-resize?
```
> sudo resize2fs /dev/md0
resize2fs 1.40.2 (12-Jul-2007)
Filesystem at /dev/md0 is mounted on /; on-line resizing required
old desc_blocks = 3, new_desc_blocks = 19
Performing an on-line resize of /dev/md0 to 76862960 (4k) blocks.
The filesystem on /dev/md0 is now 76862960 blocks long.
```
I've also emailed the author of the first reference post ("MKF blog") and asked him why he thought it necessary to do all those extra steps.

P.S.  I've updated my original instructions to include 'sudo'

---

