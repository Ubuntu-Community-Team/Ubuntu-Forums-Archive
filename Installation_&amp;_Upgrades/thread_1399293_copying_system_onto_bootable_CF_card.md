---
title: "copying system onto bootable CF card"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by aubuti on 2010-02-05
I have seen pieces of what I need addressed in various threads, but nothing that puts them all together. Any help on this will be much appreciated.

I am running 8.10 desktop on an MSI Wind desktop. Everything is on the single 500GB hard drive. I also have a 4GB CompactFlash card in the system that has a working version of 8.04 desktop on it. I would like remove 8.04 from the CF card and copy/clone the currently configured 8.10 onto it as a backup just in case I accidentally trash the 8.10 installation on the HDD some time. I'd also like to be able to update the CF backup easily periodically to keep it current with the setup running off the HDD.

The HDD is partitioned as follows. 

```

ken@pinot:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2              9843308    800448   8542840   9% /
tmpfs                  1032220         0   1032220   0% /lib/init/rw
varrun                 1032220       376   1031844   1% /var/run
varlock                1032220         0   1032220   0% /var/lock
udev                   1032220      2740   1029480   1% /dev
tmpfs                  1032220        12   1032208   1% /dev/shm
lrm                    1032220      2204   1030016   1% /lib/modules/2.6.27-16-generic/volatile
/dev/sdb1               980308    129180    801332  14% /boot
/dev/sdb10           403718328 179072156 204138400  47% /data
/dev/sdb6             14263188   4954448   8584212  37% /home
/dev/sdb9              4917648    141860   4525980   4% /tmp
/dev/sdb7             19686804   2619360  16067400  15% /usr
/dev/sdb8              4917648    678512   3989328  15% /var

```
Command line is not a problem, so if the solution involves 'dd' or other command line tool that is fine with me. I've seen lots of dd examples for copying /dev/sdb to /dev/sda , but I only want to copy the filesystems necessary to boot from the CF. The /data and /home fs are regularly backed up offsite and don't need to go onto the CF, and wouldn't fit anyway.

I hope this is clear, and thanks in advance.

-K

---

### Post by lemming465 on 2010-02-07
If you really want an alternate boot device, you'll need to get the contents of /, /boot, /usr, and /var onto the CF.  I don't think it will fit in 4 GB, so you'd need a bigger CF card.  Also, you'd have to fiddle with /etc/fstab to correct the partitions and devices or UUID's to match the CF device.

Once you were set up, the simplest way to keep it updated would be using *rsync*.

---

### Post by aubuti on 2010-02-09
Thanks for the reply. Actually Hardy fit on the 4GB just fine. So I decided to do a distribution upgrade to 8.10, and had to remove some larger packages that I don't use on this computer anyway, as I use it mostly as a Squeezebox audio server. After that Intrepid installed fine as well. I still need to tinker with the filesystems a bit, as I had originally configured /var and /tmp to write to a tmpfs to avoid wearing out the CF with repeated writes to logs and such. 

Keeping it updated with the main (HDD) system via rsync is a good suggestion that I had overlooked. Thanks.

---

