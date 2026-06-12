---
title: "Very slow Win10  boot with Ubuntu 16.10 dual boot - any fixes?"
date: 2016-10-05
forum: Installation &amp; Upgrades
---

### Post by d-a-johnston-hw on 2016-10-05
The following setup is giving a very slow boot in Win10 (several minutes), whereas the Ubuntu boot is very fast (a few seconds). Grub2 is on the first SSD, secure boot is off. 

SSD1 SATA M2  UEFI/MBR   
sda1 EFI stuff 
sda2 Ubuntu  ext4
sda3 swap


SSD2 PCIe  M2 GPT
Win10  ntfs

Ubuntu was installed first on SSD1 then Win10 on SSD2. Windows  didn't show up in the grub menu after installation and running update-grub, so running boot-repair fixed that.

Any possible fixes for the slow Win10 boot, short of nuking one or both of the installations? Is the mixture of MBR/GPT giving grub or the Win10 bootloader indigestion?

---

