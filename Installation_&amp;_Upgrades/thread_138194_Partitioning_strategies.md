---
title: "Partitioning strategies"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by reech on 2006-03-01
Hiya All - 

I would like to set up a server (with large db / web server) on a 150gb raid 1 drive (2x150gb). What I'd like to know is how different partitioning strategies  (ie single / basic / with LVM ) will affect disk performance and which is likely to perform  best. 

Any ideas / suggestions /experiences ?

---

### Post by glug101 on 2006-03-01
[QUOTE=reech]Hiya All - 

I would like to set up a server (with large db / web server) on a 150gb raid 1 drive (2x150gb). What I'd like to know is how different partitioning strategies  (ie single / basic / with LVM ) will affect disk performance and which is likely to perform  best. 

Any ideas / suggestions /experiences ?[/QUOTE]
Does this RAID partition also include the system files? (/ partition?)  That's something that could eat into the performance.  Also, if I'm not mistaken, raid 1 itself eats up performance since there are double the normal number of writes to the drive.  I would imagine this to be quite a bottleneck if you have a high use DB on the partition.

If this is mission critical information and performance is an issue, I would recommend a raid 5 setup.  That way you would have the same chance of data loss (compared to RAID 1) but you would not see no hit to performance.

---

### Post by reech on 2006-03-06
Thanks for the reply - 

Think I'll be sticking with R1 though - I need the redundancy and the double read speed would be a real help.

Anyone have any ideas on the performance hit LVM would have on such a system?

thx -

---

