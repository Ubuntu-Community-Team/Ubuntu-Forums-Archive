---
title: "Force install on disk with bad sectors?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by words1 on 2009-12-07
I'm trying to install Ubuntu on an ancient Dell Inspiron 3500, which I have done before.  I have tried every recent version of Ubuntu and Xubuntu, but the installation always halts because of bad sectors on the target disk.  I can install Windows XP on the disk with no problem.  Is there a way to force the Ubuntu installation to proceed, ignoring the few bad sectors?

Or is there a repair program I can run on the disk?  I can't run fsck because the disk is "busy," though not mounted.

---

### Post by tgalati4 on 2009-12-07
Boot the live CD
Open a terminal
sudo fsck -c /dev/sda1   (Assuming that the bad sectors are on the first partition)

Try to install.

Or, buy a new disk.

---

### Post by plusnplus on 2009-12-07
Hi words1,
just curious, why you want install a system into the harddisk that you knew have bad sector?

---

