---
title: "xubuntu install partition"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-03-24
I am trying to install xubuntu to triple boot a drive that currently has Win xp ( hda1)
Mepis ( hda2) swap (hda3). I partitioned an 11 gigs with reiser for xubuntu.
When I try to set up that mount point on hda4 as /, it gives me an error saying " no root file sys.

What am I doing wrong? 

In the installer, I designated hda4 mount point as /.

---

### Post by jbd on 2007-03-25
I'll verify this problem exists on Edgy (6.10). I tried to install on a secondary drive, and ran into the same problem. It will let me delete partitions, but not add them.

If the 3 partitions on that drive are all set up as Linux (/boot), Linux (/) & swap, then it will complain that I don't have a root partition (although I've specifed hdd3 as "/").

Also, although I've told the partitioner to use drive hdd, it by default, selects partitions on hda.

Note: I'm using the 6.10 Desktop (standard Personal Computer) ISO to install with.

---

### Post by jbd on 2007-03-25
Evidently, this is a bug. The workaround appears to use the textual installer or the alternate install image. Details are in:

[https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130](https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130)

---

