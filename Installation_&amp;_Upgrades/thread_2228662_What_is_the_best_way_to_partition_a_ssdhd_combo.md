---
title: "What is the best way to partition a ssd/hd combo?"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by www2 on 2014-06-08
Any one know what is the best partition map for a ssd/hd combo?

my current idea is:
SSD (240 GB)
/ (180GB)

HDD (3TB)
/tmp (16GB)
/var  (20 GB)
swap (16 GB)
/home (3TB - the size form oder partitions)

And my question are:
1. is the /tmp to big?
2. is /var to big? ( i am not planing to run a lamp server on this system)
3. What is the best size for the swap partition?

---

### Post by oldfred on 2014-06-08
I prefer that each drive be bootable. Or have multiple / on each drive.
My 64GB SSD has two / partitions, one with 12.04 and the other now is 14.04, but I have not fully converted yet.
My working 12.04 uses 11GB including /home. Most of /home is .wine as I have Picasa and /home is about 2GB.
But I mount data partitions from rotating drive and link data folders into /home.

I want reliability. So all partitions required to boot are on the same drive. Only data and swap may then be on another drive.

On swap choices are 0 which many may suggest as you probably never will use it, 2GB which I suggest just to have some, or the size of RAM in GiB not GB so you could hibernate if desired.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive. Now new working installs are on SSD, but many test installs are on larger hard drive.

      
 suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Some like tmp in RAM, but I write DVDs and need 4GB for a DVD in tmp, but my RAM is only 4GB so I so not think that would help me.

---

