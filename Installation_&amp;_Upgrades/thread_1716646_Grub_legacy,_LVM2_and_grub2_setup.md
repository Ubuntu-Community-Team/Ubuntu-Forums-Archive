---
title: "Grub legacy, LVM2 and grub2 setup"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by fela on 2011-03-28
At the moment I have a working LVM2 setup with Arch Linux, and want to dual boot with Ubuntu.

I have a separate small-ish boot partition (ext2, /dev/sda1), and the rest of the drive is an LVM2 logical volume group (/dev/sda2). It's got **grub legacy** installed to /dev/sda, with the bootloader files and of course OS kernels and initrds on /dev/sda1. I actually have not only Arch but BackTrack and a Gentoo install lying around somewhere, they all have their kernels situated inside appropriately named folders in /boot.

So, until now, every time I installed a new Linux system it was using grub legacy, and I simply needed to move all the kernels over to a subfolder of /boot and modify menu.lst. Of course, this won't be the case with Ubuntu as it uses grub2.

I've heard of chainloading, so how can I chainload grub legacy onto a new install of grub2 which leads to Ubuntu (grub2 being installed on an LVM2 logical volume, remember)?

Cheers

---

