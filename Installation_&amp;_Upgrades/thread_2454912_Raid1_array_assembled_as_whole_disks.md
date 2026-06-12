---
title: "Raid1 array assembled as whole disks"
date: 2020-12-08
forum: Installation &amp; Upgrades
---

### Post by gian on 2020-12-08
Hello All,
I have now rebooted my 20.04 box and the RAID1 array was lost.
Googled around, and it comes out that this can happen if the array is assembled with whole disks /dev/sdb, and not partitions, i.e /dev/sdb1.
Although I am sure I had followed a trusted tutorial, it seems true: fdisk -l doesn't show partitions.
Now the array is on, I see my files, and it is currently re-syncing.
The question is: what should I do? move all the data (almost 4TB) elsewhere, create partitions, and move the data back?
I am sure it worked fine for months with this setup.
Thanks for your time and comments,
-Gian

---

### Post by rsteinmetz70112 on 2020-12-08
In order of increasing safety:

1. The rather obvious thing to do it backup your array, reconfigure your existing drives and restore the array. You can get 4 TB drive for a little more than $100. Depending on the setup you may be able to get by with more smaller drives. This has the advantage or not requiring your to shutdown the existing array risking not being able to get it going again before you have a good backup..

2. Alternately you can get 2 new drives, configure them, add them to the array and sync them. You new drives will need to be a little bigger than your existing drives. 

3. OR you can get two new drives create a second array and transfer your data to the new array.

There are probably other alternatives

---

