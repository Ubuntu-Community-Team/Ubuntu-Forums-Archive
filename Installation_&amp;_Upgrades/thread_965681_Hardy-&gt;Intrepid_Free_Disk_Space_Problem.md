---
title: "Hardy-&gt;Intrepid Free Disk Space Problem"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Schiz0 on 2008-10-31
I'm trying to upgrade from Ubuntu 8.04 to 8.10. During the upgrade process, I'm getting an error about free space:

The upgrade needs a total of 502M free space on disk '/'. Please free an additional 40.5M of disk space on '/'.

"df" shows that I have 440M available on / currently. What can I do to free up more space? I already emptied by trash and ran "apt-get clean".

/, /home, /var, and /tmp are all on separate partitions on my HDD. The other three have plenty of free-space. Can I somehow extend the / partition?

Thanks.

---

### Post by chrisdeckard on 2008-10-31
Unless you have free space on the disk somewhere to copy / to, or unless you are using LVM, you are kinda SOL I think.  I would be interested to see you post the results of du -sk /*.  That'll give a printout of each root directory and what's in it.  apt-get clean won't help you if /var is a separate partition.  If /tmp is a separate partition, then you may actually have something in the "real" /tmp and something is taking up space there.

-Chris

---

### Post by anystupidname on 2008-10-31
You could use this:
[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127)
to resize the partition(s)

---

