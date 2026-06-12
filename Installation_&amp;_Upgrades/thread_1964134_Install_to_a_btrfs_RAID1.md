---
title: "Install to a btrfs RAID1?"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by JoeGoalie on 2012-04-23
When 12.04 releases Thursday it has btrfs as an option for fs.  I know it is marked experimental still, but I still wanted to try it out for the snapshotting and the drive pooling that you can do with the way it does RAID.  Knowing a little about btrfs I tried using the alternate install cd to install Ubuntu 12.04 beta on a disk with btrfs. I also created an exact same partition size on a second disk. If I try to add the second disk partition when booted into the OS it adds it as RAID0 with RAID1 metadata, I want all RAID1. If I try to boot a live cd and then make it RAID1 and rebalance, it works but won't boot afterwards. Is it possible to isntall Ubuntu on a btrfs RAID1?  I got to imagine it's possible, I'm betting it's an edit in the /etc/ftsab I would need to make after creating the RAID1 during th live CD session.  Any ideas would be appreciated.

---

