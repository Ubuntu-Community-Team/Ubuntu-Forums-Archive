---
title: "Ubuntu not auto detecting one of my soft raid"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Grooby on 2010-01-10
Hi All,
My home linux box's main drive died.  With that, I decided to switch from Gentoo to Ubuntu 9.10.  The original box has 2 RAID5 partition.  MD0 is made out of 6x 200GB PATA drives where MD1 is made out of 4x1TB SATA drives.  After I install Ubuntu, MD1 comes up and detected fine by the OS, however, MD0 failed to came up.  "/usr/share/mdadm/mkconfig" shows that MD0 had 2 different configurations.  I decided to backup my MD0 data, zero-out the all the HDs (using dd if=/dev/zero of=/dev/sd[f~g] bs=1M) and rebuild the RAID5.

Now that MD0 has been rebuild and mkconf shows only 1 UUID for it, it still does not come up automatically after reboot, even though MD1 does.  Running "mdadm --assemble --scan" will pick up and start the RAID.


Now I am really at a lost on why this is happening.  Never really encounter this problem when I was using Gentoo.  I believe this must be something very simple that I have missed.

Any help, suggestions are welcome and thanks in advance.

- Jon

---

