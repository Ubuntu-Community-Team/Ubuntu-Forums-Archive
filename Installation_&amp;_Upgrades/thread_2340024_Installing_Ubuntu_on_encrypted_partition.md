---
title: "Installing Ubuntu on encrypted partition"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by rschanzenbacher on 2016-10-15
First, sorry if this makes no sense as I am very tired and going to bed. I am trying to install Ubuntu on another hard drive in my PC. The first hard drive had Ubuntu 16.04 LTS dual booted with Windows 10. There second hard drive had absolutely nothing on it. I get to manual partitioning screen. Setup a boot partition so I can move the HD to another PC. I create the first partition that's encrypted. It gives me the famous unsafe swap error. I deleted the swap from my main Ubuntu install on the first hard drive as it kept remounting itself. I create 2 encrypted partitions and an unencrypted home partition. At this point the hard drive had a boot, 2 encrypted partitions (One being the main / mount point and the other being encrypted swap), and a home partition. It finally let's me continue but when I get to the actual slideshow part while installing it gives me the error, "the attempt to mount a filesystem with type ext4 in encrypted volume failed...." Then gets stuck at "creating an ext4 partition on /dev/sdc5 as /home" and won't progress.

Any ideas? Thanks in advance for your help with this.

---

### Post by sudodus on 2016-10-15
It is very important to avoid mistakes that leave security holes, when you create an encrypted system. For that reason I suggest that you let the Ubuntu installer create the system automatically, and accept the configuration created.

It is easiest to get things correct, if you remove all other drives and have only the live drive (from which to install) and the target drive (to which to install) connected. This is particularly important in UEFI mode.

Then start the installer, and at the partitioning window, you should select LVM with encryption. It will create a system with

- [an EFI partition in UEFI mode]
- an unencrypted boot partition
- an encrypted partition
- and in the encrypted partition an  LVM root partition and an LVM swap partition.

You can use the following instruction for testing to help you make the installation correctly,

[Install (entire disk with lvm and encryption) in Ubuntu Desktop amd64 in Xenial Daily](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/133317/testcases/1451/results)

---

