---
title: "Ubuntu in Windows -&gt; dual boot"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by al2222 on 2010-03-19
Hi,
I installed Ubuntu 9.10 to Windows on trial. I am very satisfied after two months of usage and now I want to install it as a second system. 

I have these "problems":
1, I don't want to start from zero and repeat all process of setting desktop and adding another application and packages.
2, I have notebook Compaq 6715s and I use kernel 2.6.31-14-generic. Newer versions of kernel, which came as update, didn't work. So I have to use this version.

Is it possible to safe actual installation, create proper file system on disk and copy/move  Ubuntu to disk?

Regards!

Alex

>uname -a
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

>sudo fdisk -l
dev/sda1   *           1        4547    36515745    7  HPFS/NTFS
/dev/sda2            4547        8591    32484415+   f  W95 (LBA)
/dev/sda3            8591        9527     7518208    7  HPFS/NTFS
/dev/sda4            9527        9730     1627136    7  HPFS/NTFS
/dev/sda5            4547        8591    32484352    7  HPFS/NTFS

>sudo df -h
/dev/loop0             15G   11G  2,9G  79% /
udev                  436M  268K  436M   1% /dev
none                  436M  136K  436M   1% /dev/shm
none                  436M  200K  436M   1% /var/run
none                  436M     0  436M   0% /var/lock
none                  436M     0  436M   0% /lib/init/rw
/dev/sda5              31G   19G   13G  61% /host

---

### Post by bigpayne69 on 2010-03-20
not sure how new you are to this but you could just use a G-Parted Live disk and copy your Ubuntu partition from the hard drive of you old computer to your new one. If you do, you may have to make that the new partition is in the same partition order as your old one otherwise grub will give you an error when you try to boot.

---

### Post by al2222 on 2010-03-21
> **bigpayne69 said:**
> not sure how new you are to this but you could just use a G-Parted Live disk and copy your Ubuntu partition from the hard drive of you old computer to your new one. If you do, you may have to make that the new partition is in the same partition order as your old one otherwise grub will give you an error when you try to boot.

I have only one computer. I have Ubuntu as application in Windows on disk partition /dev/sda5 with HPFS/NTFS file system.

---

