---
title: "out of disk space on ubuntu"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by kahnoie on 2010-08-21
I am nearly out of disk space on ubuntu installation and I need help.
/dev/sda6     ext4     24G   22G  1.5G  94% /
/dev/sda7     ext4    8.3G  5.0G  2.9G  64% /backups (there was some free space so I created this)
none      devtmpfs    1.5G  356K  1.5G   1% /dev
none         tmpfs    1.5G  4.6M  1.5G   1% /dev/shm
none         tmpfs    1.5G  424K  1.5G   1% /var/run
none         tmpfs    1.5G     0  1.5G   0% /var/lock
none         tmpfs    1.5G     0  1.5G   0% /lib/init/rw
/dev/sda1  fuseblk     25G   12G   14G  46% /media/New Volume____ (windows E:)

1. I would either like to include /backup within / itself. Is it possible? If so, how?

2. I would like to take a backup of my ubuntu installation, reformat my disk, and install ubuntu from the backup on a bigger partition. Is this possible?  Is it possible? If so, how, especially when the partition stable would have changed completely?

3. Any other alternatives?

Thanks in advance,
Amit

---

### Post by sharathcshekhar on 2010-08-21
1. I dont think you can merge partitions like that. How ever you can use Gparted to grown your partitions. I see that your / and /backup physically are next to each other. So boot from a live Cd, open Gparted, delete /backup partition and resize / partition. Make sure it is not mounted.

Please note, all you data in /backup will be deleted but / will be safe. However taking a back up is strongly recommended.

2. You can use a software called remastersys which can take a back up of your system with settings onto to a iso image. You can reinstall from that.

---

### Post by Rubi1200 on 2010-08-21
After backing up but before you reinstall, you might also want to try cleaning out the system a bit and see if that helps:

[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

---

