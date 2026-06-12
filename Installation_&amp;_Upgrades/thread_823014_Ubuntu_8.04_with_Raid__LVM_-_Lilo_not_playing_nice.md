---
title: "Ubuntu 8.04 with Raid / LVM - Lilo not playing nice"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by omorley on 2008-06-08
I snagged the alternate install disk, setup raid, lvm, etc. no problem however lilo wouldn't install properly.
/dev/sda = main storage array
/dev/sdb and /dev/sdc are the two drives which I'm using in raid1 for my system.

Dropped to the command line, did a manual liloconfig and got the following error:

Cannot proceed. Maybe you need to add this to your lilo.conf:
disk=/dev/sdb inaccessible
(real error shown below)
Fatal: VolumeID read error: sector 0 of /dev/sdb not readable


I followed the error's directions and threw "disk=/dev/sdb inaccessible" in the lilo.conf

Unfortunately this didn't solve the issue, any ideas?

---

