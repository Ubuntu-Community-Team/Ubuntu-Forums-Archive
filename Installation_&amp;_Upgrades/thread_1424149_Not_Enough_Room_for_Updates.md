---
title: "Not Enough Room for Updates"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by terrybennett on 2010-03-07
I had to re install 9.04 yesterday after messing up my system.   I tried to update to 9.1 but the tochpad would not work and my attemps to fix the problem left me with a system that would not boot.

 I have a dual boot Vista and Ubunt 9.04.  Everything went fine on the re install of 9.04  but now when i try to run the updater it says I need 485 MB of disk space.   I have 2 GB left on the operating system partition and 1.5GB  on a Home partition.  It says there is not enough room on disk \.

I am absolute beginner.  I was able after the re install to get my \Home partition set up so I suspect something is not pointing to the correct place.  

I just want to get my systme back where I was with 9.04

---

### Post by oldos2er on 2010-03-07
Can you run **sudo fdisk -l** in a terminal and post the output here?

---

### Post by terrybennett on 2010-03-07
terry@terry-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29e3de20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         128     1028128+   7  HPFS/NTFS
/dev/sda2   *         129       13376   106414560    7  HPFS/NTFS
/dev/sda3           13377       14334     7695135   83  Linux
/dev/sda4           14335       14593     2080417+   f  W95 Ext'd (LBA)
/dev/sda5           14335       14593     2080386   83  Linux
terry@terry-laptop:~$

---

### Post by oldos2er on 2010-03-07
Can you also post the output of **df -h** ?

---

### Post by terrybennett on 2010-03-07
terry@terry-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.3G  7.1G     0 100% /
tmpfs                 438M     0  438M   0% /lib/init/rw
varrun                438M  104K  438M   1% /var/run
varlock               438M     0  438M   0% /var/lock
udev                  438M  156K  438M   1% /dev
tmpfs                 438M  660K  437M   1% /dev/shm
lrm                   438M  2.4M  436M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5             1.7G  584M  1.1G  36% /home
overflow              1.0M   12K 1012K   2% /tmp


Okay I don't  know what is going on.  It looks like  sda3 is full.  I formatted before installing from the disk.  The partition was not re sized.  Why is that partition full?    I don't know what to look for or what to delete.

---

### Post by terrybennett on 2010-03-10
I formatted and enlarged my root partition to 8.3 GB.  I did a clean install of 9.10.  After two days it again says I am running out of space.  What am I doing wrong?  Most everything I read says Ubuntu can be installed on 5 GB.  Home is on its own partition.

---

