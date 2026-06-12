---
title: "Warning about logical sector size 4096 during install"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by jeso on 2008-11-07
During installation I am warned by the partitioner that the support for the logical sector size 4096 is highly experimental.

The 1TB HD also contains two Vista partitions, 60G + 900G, and there's also 20G of free space I've freed up for Ubuntu.

So the question is: will Ubuntu install properly, without damaging other partitions?

Here is the output of 'df -l', if it helps:
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  2027492      2380   2025112   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  2027492      2380   2025112   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                  2027492         0   2027492   0% /lib/init/rw
varrun                 2027492       104   2027388   1% /var/run
varlock                2027492         4   2027488   1% /var/lock
udev                   2027492      2860   2024632   1% /dev
tmpfs                  2027492       104   2027388   1% /dev/shm
rootfs                 2027492     54024   1973468   3% /
/dev/scd0               715810    715810         0 100% /cdrom
/dev/loop0              691712    691712         0 100% /rofs
tmpfs                  2027492        16   2027476   1% /tmp
/dev/sda2            905079800 728549440 176530360  81% /media/disk
/dev/sda1             51199996  34981468  16218528  69% /media/disk-1

---

