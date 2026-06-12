---
title: "Ubuntu update from 12 to 14 on dual boot with Win 7"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by MikRose on 2015-04-07
I have Ubuntu 12.04 and Win 7 dual-booting.  I want to update Ubuntu to 14.04 and leave Win 7 alone.  Is the best way to use OS Uninstaller on Ubuntu 12, then install 14 from CD?

---

### Post by ubfan1 on 2015-04-08
I generally prefer the clean install, but I did update a 12.04 to 14.04 pretty easily.  I assume we are talking about a network update/upgrade to get the 14.04, not the "reinstall Ubuntu"="wipe the disk" from the CD.  Backup both systems first, since bad things can happen.  The "uninstall" you refer to is unknown to me, I would just select the "something else" from the CD, select the existing Ubuntu root for the new root, and check off the format (assuming you have backed up all your personal data).

---

### Post by Vladlenin5000 on 2015-04-08
I've been saying this quite a lot lately, sometimes here and many times on other venues, some people get it, others don't: You don't need to 'uninstall' operating systems; OSs reside in partitions that once deleted or reformatted whatever was in those partitions is gone.
Any OS installer media, Windows, Linux or others, is (usually) sufficient to manage partitions. Granted, Windows installer can't properly recognize typical Unix/Linux file systems but it doesn't have to... It can't be installed on those file systems so whenever one needs to install Windows, one needs to have at least one NTFS partition that can be created and formatted by Windows; previous partitions can also be removed by the installer.

Likewise for an Ubuntu fresh install:
You can boot the intended Ubuntu installation media and, as suggested above, select "Something Else..." and use the same partitions you already have with the older Ubuntu release. Yes, you must be careful in selecting those partitions and, as always, HAVE A BACKUP.

---

