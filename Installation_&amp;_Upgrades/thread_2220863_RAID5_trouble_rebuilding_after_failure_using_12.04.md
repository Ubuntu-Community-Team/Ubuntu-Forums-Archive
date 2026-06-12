---
title: "RAID5 trouble rebuilding after failure using 12.04"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by pmljr on 2014-04-29
I have been running a file server using software RAID5 with Ubuntu 12.04 for several years.  I am using 3-320GB western Digital HDD in a Kingwin KF3000 hot swap rack connected to MB using SATA cables.  I have a RAID5 array setup for the OS & the files, and a RAID0 array for the swap.  

It has performed well over the years except the occasional "disk failure" which so far has always turned out to be SATA failures.  I believed the problem to be one of the SATA controllers on the MB and finally replaced the MB last year.  Unfortunately I still have "disk failures" every 6 months or so.  My skills in Ubuntu (or Linux for that matter) are weak, so previously I have always just wiped the drives and completely reloaded the OS (Ubuntu 12.04) and set up the RAID arrays from scratch each time.  I just didn't know mdadm well enough to fix it otherwise.

So I just had another failure this past weekend but this time decided to try to fix the problem.  I booted to the Alternate install CD (I always work command line only) and went to "Rescue a Broken Disk".  I found the two RAID arrays and started a terminal as root in the RAID 5 array.  I figured out how to remove and then add back in the "failed" HDD and the system rebuilt itself.  Great.  Then the next morning the system failed again.  I am suspecting an intermittent problem in the SATA cables or (less likely) the hot swap rack and think maybe I'll just replace all of them, but it the mean time I am trying to rebuild the array.

Here is where I'm stumped.  I boot to the alternate CD, select "Rescue a Broken Disk", but when I get to the screen where I pick the RAID5 array /dev/md127, it is no longer there.  And the RAID0 array /dev/md126 is also gone.  There is an option to "Assemble RAID array" but it doesn't seem to work. I can see individual partitions: sda1, sdb1, sdc1 (were for RAID5), and sda2, sdb2, sdc2 (for Extended), sda5, sdb5, sdc5 (were for RAID0).  To compound my problem I swapped the disks a few times and tried some commands I didn't fully understand so I bet I messed up the mdadm.conf, but since I can't get a terminal in the array I can't see my mdadm.conf file.  

Since I can't start a terminal on any of these partitions, I can only get a busybox on the CD.  Is there some way to assemble the RAID5 array from the busybox?  Can I recreate the RAID arrays without reloading the OS and starting from scratch?  I don't have anything super critical on these disks but I want to learn how to recover properly.  Do I mount the partitions and then try to assemble the arrays?

---

### Post by pmljr on 2014-05-14
Answering myself...
Yes, I can assemble the array from a busy box.  /dev/md127 & /dev/md126 are aliases of some kind and not the names of the array used by the mdadm.conf file.  The RAID 5 array is called /dev/md0 (on my system) and the swap array is RAID 0 and called /dev/md1.

I had to assemble the RAID 5 array and sure enough it started re-synching.  Initial attempts to assemble didn't work and I had to "force" it.

```
mdadm --assemble --force /dev/md0 /dev/sd[abc]1
```

I could not assemble the RAID 0 array because the /dev/sdb5 superblock was missing.  Since I didn't need the data on the partition I just re-created it like this:

```
mdadm --create /dev/md1 level=0 raid-devices=3 /dev/sd[abc]5
```

This worked fine - I guess the superblocks were rewritten.  I rebooted and am back in business.

---

