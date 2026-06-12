---
title: "Upgraded to Dapper, now raid will not boot on new kernel"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by glave on 2006-11-27
I recently did a dist-upgrade on a breezy server install to dapper. My system was a raid1 for the boot volume, but when she boots up now, I get this error:

```
Mounting /dev/md0 on /root failed: No such device
Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Mounting /sys on /root/sys failed: No such file or directory
Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

And then I'm dropped out to a shell. If I use the grub menu and boot the older kernel from Breezy, it works just fine. I also noticed after rebooting, that I had received an email during my upgrade, whether it pertains to this, I'm not sure

```
WARNING! If you are using hard disks which have a md superblock from an
earlier installation in a different RAID array, you MUST zero the
superblock before activating the autostart feature.

To do this, do not start the RAID devices automatically. First, zero the
superblock (mdadm --zero-superblock /dev/mdX). Next, use `dpkg-reconfigure
mdadm` to reactivate the autostart feature.
```

Would this be kernel related? Any direction?

---

### Post by glave on 2006-11-27
Anyone know if the dapper kernel has raid compiled into it?

---

### Post by glave on 2006-11-30
Still working on this if anyone can help! :)

---

