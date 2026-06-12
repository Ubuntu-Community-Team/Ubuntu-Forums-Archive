---
title: "The second hard drive can't be detected"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by tytsama on 2012-12-07
Hey guys~

There are 2 SSDs in my laptop, my Ubuntu OS is on one of them, however, I can't detect the other one =(

My laptop has a storage of 128G and had a win7 OS initially.
A few weeks ago, I wanted to add Ubuntu to it, but the installation of grub always failed. Later I found out that the storage consists of two identical SSDs and that they formed a raid system, which might  cause the installation problem.

I entered BIOS and deleted the raid volume, Win 7 and all the data were gone. Then I was able to install Ubuntu on one of the two drives, but the other one can't be detected in Ubuntu!! I try to install win7 now, and the it says that no driver can be detected!

Is there any suggestion you can offer me?? I would appreciate it a loooooooot!

Can you believe it??  A laptop with 64G storage!! It now looks like a Surface Pro transformer, a really lousy one

---

### Post by darkod on 2012-12-07
If you had a fakeraid of two disks, you should first change the sata mode in bios from RAID to AHCI (I guess you already did that).

After that it's better to remove raid meta data leftovers from both disks. You can do that from ubuntu (or from ubuntu cd live session) in terminal:
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb

That should get rid of the meta data so there are no confusions in the future.

If a disk is not shown, you first need to double check in bios whether it's detected correctly. If it's not, the OS won't be able to see it also.

After that, you can check from ubuntu all disks that are detected and their partitions with:
sudo parted -l (small L)

First double check that bios and ubuntu can see the disk, after that you can focus on win7.

---

