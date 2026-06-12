---
title: "Upgrade Hoary-&gt;Breezy causes LVM+RAID1 massive corruption"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by jmbarbier on 2005-11-23
Hello

i was running hoary on amd64, with a /home and /backup partitions mounted from LVM + RAID1 partitions... decided to dist-upgrade to breezy, everything worked well... up to reboot, where all my LVM+RAID1 partitions became massively corrupted...

I've lost all my data... but had backups...

This can be VERY DANGEROUS !!! so if you run Hoary with LVM + RAID1, be careful when upgrading (or don't upgrade !)

Investigations on the reasons of this crash are welcome...

Bye...
JMB

---

### Post by skylark on 2005-11-23
This happened to me too... (LVM on software raid1 using XFS).

I thought I lost all my data (I couldnt even mount affected partitions, which was everything except luckily my root partition which I kept on a seperate raid array using ext3).

I did some googling and found it was related to some kernel bug somewhere related to this specific combination.

Anyway, I managed to fix it using xfs_repair. As far as I can tell I suffered zero data loss (I keep iintegrit checksums on most of my files, and everything verified fine).

So there may be hope for you yet.

I never posted about my problems since I thought no-one else would have my config.

---

### Post by jmbarbier on 2005-11-25
Lucky you !! 
but repairing my ext3 was unsuccessful... (leaved very few files)... will try XFS one day perhaps...

do you have references for this kernel bug ??

---

