---
title: "Resizing a JFS partition with gparted - resized partition still shows old size"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by Lido on 2013-06-14
I just got a bigger hard drive and used the 13.04 live cd (actually DVD since it was a bit too big for a cd) to clone the old drive and enlarge a partition that I use to store most of my files (which happened to be formatted with the JFS filesystem). I followed a pretty straightforward how to guide that explained how to use dd to clone your drive and then another one explaining how to use gparted to resize the partition(s). The problem was that after resizing, rebooting, going back to the live cd and running fsck a few times, my system still saw the resized partition as its old size. After a bit of searching I found a thread where someone mentioned the following little bit of magic which apparently only applies to JFS partitions:
```
sudo mount -o remount,resize
```
After running that command, the system seems to recognize and display the full/new partition size in system monitor and df. Hope that helps someone else!

---

