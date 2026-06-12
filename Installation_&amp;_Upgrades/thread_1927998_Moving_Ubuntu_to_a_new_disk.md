---
title: "Moving Ubuntu to a new disk"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by jds340 on 2012-02-19
When I first installed Ubuntu I thought I'd be clever and put the system stuff on one partition and my home directory on another. I now realise that was a mistake because I get bad use of the space on the drive.

So I'm now moving it all to a single partition on another drive. I've created the single partition and now want to copy stuff across so that I can boot from the new drive.

If the new partition is set up as a master boot partition what else do I need to have in place so I can boot from the new drive?

Thanks

John Small

---

### Post by darkod on 2012-02-19
Actually having a separate /home is the better option.

If you give some details and why you think you made a mistake, maybe someone can come up with some advice.

Also, it seems you are not looking to simply move ubuntu as the title implies. Do you want to "join" the root and /home partitions in one?

---

### Post by Bucky Ball on 2012-02-19
/home partition is good, as mentioned, though not everyone agrees. It means if you break your system irreparably or if you need/want to reinstall Ubuntu for any reason you can do so without altering or losing all the data in your /home partition.

If your mistake is simply that you are unhappy with the way your drive is partitioned, why not just shrink and expand your partitions to how you want them?

To do this, boot from the LiveCD, 'Try Ubuntu', once at the desktop open 'Partition Editor' (Gparted), then simply shrink, expand and resize partitions. It must be done from the LiveCD as partitions must be unmounted and it is impossible to unmount / if you are running Ubuntu from it, obviously. 

Good idea to back up any valuable data before attempting this in case something screws up (you make a mistake!). Post back with any questions. ;)

---

