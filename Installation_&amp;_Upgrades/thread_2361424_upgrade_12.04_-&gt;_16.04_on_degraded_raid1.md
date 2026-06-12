---
title: "upgrade 12.04 -&gt; 16.04 on degraded raid1"
date: 2017-05-16
forum: Installation &amp; Upgrades
---

### Post by thomas-toniazzo on 2017-05-16
I need to upgrade from 12.04 to 16.04; I am currently sitting on a degraded RAID1 array (one disk failed):

~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb6[1]
      40381312 blocks super 1.2 [2/1] [_U]
      
md3 : active raid1 sdb7[1]
      41028480 blocks super 1.2 [2/1] [_U]
      
md2 : active raid1 sdb9[1]
      2638384960 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sdb5[1]
      210039616 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>

my questions:
 . will the upgrade handle RAID1? I have read that only the server installation supports RAID for 16.04; I currently have a desktop installation.
. if not, do I have to revert to non-RAID disks before upgrading?
. if yes, does the degraded array pose additional problems when upgrading? i.e. had I better rebuild before or after upgrading?)
. also: is it perhaps advisable to upgrade first to 14.04, then to 16.04

Any advice much appreciated

---

### Post by TheFu on 2017-05-16
I would assume everything will break and backup everything I need.

A broken RAID setup won't get better. Fix that first.  I would assume it will be trash if currently broken, probably leaving your system in an unusable state.

Get your 12.04 system as patched and updated as possible.  Really, I'd wipe it and start fresh. Enough things have drastically changed in the least 5 yrs to make bringing all the cruft from a 12.04 system forward counter productive.

Backups are 1000x more important than RAID. RAID never replaces the need for backups.  RAID solves 3 issues. No more.  Backups solves 1001 issues, including broken RAID issues.

---

### Post by thomas-toniazzo on 2017-05-17
what makes you think I'm not running back-ups. 
Please, I just need (factual) answers to my questions. 
Any other takers, please?

---

### Post by TheFu on 2017-05-17
> **thomas-toniazzo said:**
> what makes you think I'm not running back-ups. 
Please, I just need (factual) answers to my questions. 
Any other takers, please?

The combination of things posted above and elsewhere (commonly seen issues) got me thinking. Sorry.
I will never post to you again.

---

