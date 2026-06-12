---
title: "Dual Boot Uefi Install"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by mindcrusher on 2014-03-10
I recently received a laptop (lenovo S440) that came with windows 8.1 (64 bit) preinstalled on the SSD disk. I want to install Ubuntu and have a dual boot machine, but I need not to alter in any way the windows instalation. 
For this I created a separate partition on the SSD drive (and the associated swap). If I am to leave the default boot loader unchanged I want the linux boot loader to be installed on a separate USB stick (or an SD card). However I am unable to do this at this moment and I have no idea on how to do this. 

Could anyone help me with this? I am not a total noob on linux but I never installed the OS on an UEFI system.

---

### Post by oldfred on 2014-03-10
The boot loader will install to a separate folder in the efi partition. So at anytime you can directly boot either system from UEFI menu.

But if you want to boot from a flash drive, you have to format it with gpt partitioning and make first partition the efi partition with gparted and install grub to that partition.

---

