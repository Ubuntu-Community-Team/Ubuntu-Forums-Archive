---
title: "df shows fuse in use for / ?"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by twinspop on 2008-09-05
When I run df i see:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            478702256  79870012 374707032  18% /
varrun                 1879572       360   1879212   1% /var/run
varlock                1879572         0   1879572   0% /var/lock
udev                   1879572        64   1879508   1% /dev
devshm                 1879572      1272   1878300   1% /dev/shm
lrm                    1879572     45040   1834532   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1            484535504  94456784 365659520  21% /driveb
gvfs-fuse-daemon     478702256  79870012 374707032  18% /home/luser/.gvfs
```

I'm concerned because heavy disk use brings my system, Q6600 with 4GB of RAM, to it's knees. Also, other 8.04 systems I have are lacking that entry. Am I running my whole OS through fuse? How could this happen?

Maybe I'm just a wee slow on this Friday...

Thanks,
tp

2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

---

### Post by twinspop on 2008-09-07
The rescue partition was the culprit I think. I ran gparted and saw the 6GB rescue partition still there -- formatted as NTFS. It is the first partition on the drive. I backed it up:

# dd if=sda1 of=rescue_img.dd

Then used gparted to format the partition as ext3. A reboot brought up a root partition with no fuse involved.

I haven't had time to investigate how drive use impacts performance, but I'm hopeful this will address it.

---

