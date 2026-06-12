---
title: "Perplexed install-Dapper/XP dual boot"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2006-11-18
Help needed please!

I'm following this ([http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)) guide for dual boot which I've done before but this is on a new laptop.  When I get to the point of choosing how to partition the disc, I only get 2 choices:
   1. Erase entire disk: SCSI 1(0,0,0)(sda)-160GB ATA Hitachi HTS54161
   2. Manually edit partition table.

I _don't_ get the option:
   Resize IDE 1 Master,partion #1 (hda1)and use freed space.

...even though WinXP(MCE) is already installed.
If I continue to manually edit, I get a large 149GB space to use.  If I press on, it prepares mount points with swap of 3GB and / of 65GB and I can't change those values.  I'd prefer swap of 4GB (RAM=2GB), / of 10 to 20 GB and /home the leftover.

Any ideas would be greatly appreciated!  Also note, the original Dell installed software was removed & XP reinstalled so as to remove the bloatware--I need XP for limited work related software.
Thanks--sorry so lengthy!

---

### Post by confused57 on 2006-11-18
You might want to try the gparted live cd(30 mb) to resize your Windows partition(if you haven't already done so):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

It's a later version of gparted and would probably work better for resizing NTFS partitions.  With 2 GB of ram, you probably don't need a swap partition...you can just choose to manually partition the free space during install.  The gparted live cd is a great partitioning program & may help.

I'm not sure why you can't change the root partition size of 65 GB, I've always installed with the alternate cd, so I'm not really familiar with the desktop installer.

---

