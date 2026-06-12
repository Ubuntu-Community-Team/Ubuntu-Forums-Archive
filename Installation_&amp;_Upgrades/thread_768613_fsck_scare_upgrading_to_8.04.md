---
title: "fsck scare upgrading to 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by bkline on 2008-04-26
Posting this here in the hopes that it might help others who got bitten by this.

I just upgraded my workstation in place from gutsy to hardy, and most things went pretty smoothly until the reboot, when I got dumped into a shell with an fsck failure on the partition where I store my nightly backups for all my systems.  It turned out that the device where the partition lives had been renamed by Ubuntu.  What used to be /dev/hdb was now /dev/sdb.  Once I realized what had happened, all I needed to do was edit /etc/fstab and change /dev/hdb4 to /dev/sdb4 and remount the partition.

HTH.

---

