---
title: "Install ubuntu keeping old xfs partition"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by Pipette Monkey on 2007-01-18
Hello,
   I have a computer running Fedora Core 4 that I would like to upgrade to edgy.  However, I have a large XFS partition mounted on /video that I would like to keep and have mounted on the same directory in edgy.  I was wondering what I should do when installing to keep this setup.  my partition table currently looks like
 Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          13      104391   83  Linux
/dev/hdc2              14        1543    12289725   83  Linux
/dev/hdc3            1544        1608      522112+  82  Linux swap / Solaris
/dev/hdc4            1609       38913   299652412+   5  Extended
/dev/hdc5            1609       38913   299652381   83  Linux

Thanks

---

### Post by wilderness wanderer on 2007-01-18
No problem, just use the standard livecd/desktop installer.  When it asks about partitioning, choose to partition manually.  You will be able to choose mount points as well as whether to format for each partition.

---

