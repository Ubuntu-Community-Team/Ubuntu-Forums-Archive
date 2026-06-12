---
title: "Yet another Installation problem"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by quasar66@yahoo.com on 2012-01-05
Hi...
Thanks for reading this...
I have been installing Ubuntu, till 11.04 without any major hassles, and consider myself fairly worn out campaigner on this subject. However, now am stumped. So need advice.

My system has 3 HDD's, of 1TB each, which the first two are on SATA 6GBps port, and have a Windows Installation. The third HDD (/dev/sdc)  is on a standard SATA port, has one windows E: partition of 350GB, which is NOT a boot partition or anything, just books repository. The second partition on this /dev/sdc is a /home Ubuntu partition that contains very valuable collection, and I do not want to lose it. Its an ext4 format partition. The rest of the space is free to play.

What I am trying to achieve - I want to install a completely self contained Ubuntu 11.10 installation on disk 3, that ignores the first two drives, ignores the first partition (Windows) of third drive /dev/sdc, then installs on the space after the second partition of /dev/sdc, and uses the second partition as /home. I do not need a dual boot, as I would make the third drive as first to show up by changing boot order in BIOS whenever I need to go to Linux. Similarly, set the first drive as first in boot order to get into Windows.

Problem: This I was able to do on Ubuntu 10.04, then 10.10. then 11.04 without any problems. However, in Ubuntu 11.10, which I started installing yesterday, ends up in grub rescue> and the linux partitions are just not visible.

Experiments already done: Installed in expert mode, specified that /dev/sdc2 is not to be formatted but used as /home, and no luck. Then, physically removed the first two Windows disks, so that the device /dev/sdc becomes /dev/sda, and since it has NOT bootable windows, just one partition, I was hoping it would be able to install. However, no luck - same grub same rescue ... a ls command states (hd0) (hd0, msdos) and no mention of the /home, or any installation partitions.

Any advice is welcome... Thanks

---

