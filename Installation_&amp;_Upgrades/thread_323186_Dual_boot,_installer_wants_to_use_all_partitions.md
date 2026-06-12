---
title: "Dual boot, installer wants to use all partitions"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by Homeschool Hacker on 2006-12-21
-Resolved-

I am trying to install Ubuntu 6.10 on a 13GB hd w/ Windows98.
I partitioned the drive as follows:
100MB
4.5GB  (for Linux)
512MB (for swap)
3GB (for Windows)
~6GB (for shared storage space)
(the first is primary, the rest are in an extended partition)

When I ran the install wizard, I chose "manually edit partition table."
I chose mount points for the Linux, swap, and storage partitions, leaving the other two partitions blank (I wanted to keep them for Windows).  The installer gave me the error message: "No mount point selected for partition 1 Disc IDE/ATA 1 (primary) [hda1]."
If I choose a mount point for partition 1, I get the same message for partition7 (which has Win95 on it).  I don't think I want to put a mount point on the Win partition.

Can someone tell me how to get around this?

I realized that the partitions were listed in drop-down menus.  I just replaced the partitions I wanted to keep with "            " from the drop-down menu, and that took care of the problem.

---

