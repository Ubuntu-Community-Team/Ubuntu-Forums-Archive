---
title: "installing Ubuntu 7.04 without grub"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by BillDozer357 on 2007-06-24
How would I install the latest Ubuntu without grub?  I will be dual-booting with XP and using Microsoft's bootloader to boot linux.

yeah yeah I know I should use grub and all, but I'm trying ubuntu for the first time, and would like to be able to remove it without any hastle if I don't like it.

Thanks in advance

---

### Post by confused57 on 2007-06-24
> **BillDozer357 said:**
> How would I install the latest Ubuntu without grub?  I will be dual-booting with XP and using Microsoft's bootloader to boot linux.

yeah yeah I know I should use grub and all, but I'm trying ubuntu for the first time, and would like to be able to remove it without any hastle if I don't like it.

Thanks in advance
Install grub to the root partition...you should be able to click on the "Advanced" button when you reach the screen to install grub, then you can enter something like "(hd0,2)" or "/dev/sda3", whatever your root partition is...I think you need grub installed to the root partition to use Window's bootloader to boot Ubuntu.

---

