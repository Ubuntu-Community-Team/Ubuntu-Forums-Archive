---
title: "Fresh Ubuntu Server 18.04 Install RAID 1 with unformatted disks"
date: 2020-03-10
forum: Installation &amp; Upgrades
---

### Post by anguis2 on 2020-03-10
I am trying to to a fresh install of Ubuntu Server 18.04 to a desktop with two new/unformatted SSD 248 GB drives. I thought that this would be easy for even me - a non-linux expert. However, all tutorials I have found have issues that I cannot get past. All I want is Ubuntu Server installed from scratch on a RAID 1 config thag is defined during install. I've tried all of these and none do the trick. Does anyone have a simple step by step for the latest Ubuntu 18.04 ?
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)
[https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios](https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios)

The farthest I got was this - but when I select "Make a boot device" it creates a 1M bios_grub partition - nothing like the 512MB in the example.
[https://calvin.me/install-ubuntu-18.04-on-raid1/](https://calvin.me/install-ubuntu-18.04-on-raid1/)

I don't need any encryption. No LVM as the two SSD's are identical and I won't be expanding this mirror/array.
Just need a simple - dummy proof example. I don't get the /boot/efi partition and in none of the examples can I get to a point to "Mount a filesystem".

---

### Post by ajgreeny on 2020-03-10
You are probably trying to install using an MBR/BIOS installation onto a hard disk that is already partitioned using GPT partitions rather than msdos partitioning.  Such a system needs a 1MB bios_grub partition which is automatically created if you choose the default installation into partitions that already exist.

Assuming you are using an installation DVD or USB, show us the output from that of command sudo fdisk -l and we can move on from there knowing more about what you have currently got on disk.

---

