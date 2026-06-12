---
title: "Install Failure - Partition"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by mpierce on 2007-01-01
I upgraded to Edgy from 6.01 LST. All seemed well; rebooted everything worked. Upgraded python and rebooted. Boot failed with couldn't find the boot sector on hd0. 

OK - loaded CD and went in and backed up everything using chroot. 

I try to re-install from scratch & manually partition. The drive is partitioned reiserfs and is a IDE/ATA. 

I create mount points & show:
 /archive 23Gb primary hda2 (reformat enabled)
/ 12Gb primary hda3
/home 39Gb primary hda4
swap 259Mb primary (reformat enabled)
/backups 112Gb primary hdb1

When I press continue is fails with error message:
   No root file system

What is the problem?

---

### Post by mpierce on 2007-01-01
Theres a problem with the intstaller
This post in the ubuntu forums worked for me:
[http://ubuntuforums.org/newreply.php?do=newreply&p=1700787](http://ubuntuforums.org/newreply.php?do=newreply&p=1700787)

---

