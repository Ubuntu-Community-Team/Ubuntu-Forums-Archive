---
title: "Attempting to mount Empty RAID partition to /var"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2012-07-27
So I've successfully mounted my own partitions /md0p1, /md0p3 to folders I've created in the root (i.e. /srv or /backup).  I've also edited fstab accordingly.  All that is tested and done.

Now, how would I go about mounting /var from /dev/md0p2?  I can get it mounted as /var2, but I simply cannot get it to mount successfully as /var.  By that I mean when I'm in the live CD, edit fstab so it looks like:

```
 /dev/md0p2     /var     ext4 defaults    0     2
```I've also tried
```
 /dev/md0p2     /var     ext4 defaults    0 0
``````
 /dev/md0p2     /var     ext4 rw    0 0
```
Instead of taking me to the defaunt Ubuntu Unity login screen, it gives me a tty1.

---

