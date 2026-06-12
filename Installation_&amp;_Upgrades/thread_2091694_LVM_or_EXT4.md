---
title: "LVM or EXT4?"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by fullmoonguru on 2012-12-05
A while ago I was looking at changing teh size of a partition on a 2 TB drive I had on a home server/HTPC.  It was going to take days, or did take days, or something I can't remember.  But I do remember learning about LVM & how it was better for managing large disk spaces.

OK, so I'm rebuilding this PC only now I have a 120GB SSD drive for my normal partitions and the 2 TB drive just for data.  With the large drive just one big data partitions, does LVM do anything for me?  If I ever need more space, I don't see adding drives.  I'll just swap out for a 4 TB drive or something.

---

### Post by darkod on 2012-12-05
LVM is useful for combining more physical disks into one logical space. That means if you set up LVM on the 2TB disk right now, when adding another 2TB for example tomorrow, the available capacity can grow to 4TB without any data moving/copying.

On the other hand, if you would rather swap the disk with a larger one when it's full, you don't need LVM at all. However, you will need to wait for 2TB of data to finish copying when doing the switch.

Another important LVM benefit, is that "partitions" in the LVM are called Logical Volumes, and you can dynamically change their size. However, on a data disk if you are happy having one big partition, it offers no benefit for you.

---

### Post by fullmoonguru on 2012-12-05
Great, thanks for the quick reply

---

### Post by jerome1232 on 2012-12-05
Another benefit of LVM is snapshots, you can make a snapshot of a volume which basically freezes it in time, and then make a backup of the snapshot.

That way you avoid backing things up and having them change on you during the backup causing inconsistencies.

---

### Post by oldfred on 2012-12-05
Unless changing partitions around a lot LVM may not offer much.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

