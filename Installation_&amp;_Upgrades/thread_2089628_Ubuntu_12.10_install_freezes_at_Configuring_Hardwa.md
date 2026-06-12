---
title: "Ubuntu 12.10 install freezes at Configuring Hardware"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by keemax on 2012-11-29
I'm installing Ubuntu 12.10 (64 bit) from a bootable USB stick. At first I had trouble with a black screen after selecting 'install ubuntu'. I added nomodeset and xforcevesa to the options to fix that problem. Now when installing, it hangs at 'Configuring Hardware', specifically at

ubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic


Specs:

Asus UX32a DB51

Intel Core i5 3317U 1.7 GHz

4GB DDR3 RAM

intel hd 4000 graphics

500 GB harddrive with 25 GB sandisk ssd

I'm trying to install Ubuntu by itself right now on the SSD. I made custom partitions (100 mb EFI boot partition, 4GB swap space, 20GB ext4 mounted on '/')

I've tried re-downloading the ubuntu iso and creating a new boot image on my flash drive and it results in the same problem.

Thanks in advance for the help!

---

