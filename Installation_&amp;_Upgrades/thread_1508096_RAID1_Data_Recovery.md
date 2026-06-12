---
title: "RAID1 Data Recovery"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by xskull on 2010-06-12
All, 

Recently I upgraded from 8.04 to 10.04. I have a primary drive for the OS, and then some storage drives in a RAID1 setup. One of the pairs have 2 partitions and the other pair does not have any partitions. 

Since upgrading, I have not been able to reconnect with the RAID'd drives (software raid). My BIOS tells me the array is healthy, but I cannot get mdadm to mount them. 

I have no problem recreating the arrays/formatting the drives/etc, but I want to get the data on them off first. Since this is the first time this has happened to me, I want to make sure what I do (hopefully) won't corrupt the data on the drives. 

I've read that some have used a live CD to get the data back, and others "disconnected" the raid to mount just the single drive...but my lack of experience in this area causes me hold off and ask. 

Any ideas? 

Thanks
-Kevin

---

### Post by ronparent on 2010-06-13
If you truly have a raid bios you would be dealing with MB chipset implemented raid also known as fakeraid. In that case a program known as dmraid included in the 10.04 install would automatically discover the raid meta data written to the disks and make the raid partitions mountable in nautilus. That could be settled quickly by simply writing 'sudo dmraid -r' in a terminal. If there your raid bios has created meta data, than that should discover it. Otherwise you will be told there is no raid, in which case you would have to look for the softwre raid with mdadm.

---

### Post by xskull on 2010-06-13
> **ronparent said:**
> If you truly have a raid bios you would be dealing with MB chipset implemented raid also known as fakeraid. In that case a program known as dmraid included in the 10.04 install would automatically discover the raid meta data written to the disks and make the raid partitions mountable in nautilus. That could be settled quickly by simply writing 'sudo dmraid -r' in a terminal. If there your raid bios has created meta data, than that should discover it. Otherwise you will be told there is no raid, in which case you would have to look for the softwre raid with mdadm.


Thanks for the reply. I actually got the array partitions mounted again, so it seems to be somewhat working. My problem now is one drive looks to be having sector errors and they are always degraded. It doesn't seem to be trying to do anything. But most importantly, I did get a back up of everything so now I will just mess around with it and see what I can figure out. 

Thanks again!
-Kevin

---

