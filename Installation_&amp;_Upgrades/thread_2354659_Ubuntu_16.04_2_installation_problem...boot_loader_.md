---
title: "Ubuntu 16.04_2 installation problem...boot loader cannot be created on /dec/sda"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by rajsenthil on 2017-03-04
I am trying to install along my Windows 10 and replacing the existing Ubuntu. While installation I am getting issues that boot loader cannot be created. 
Please find my boot info [http://paste2.org/aM7GPhdV](http://paste2.org/aM7GPhdV)

Your help is appreciated. 


Thanks.

---

### Post by rajsenthil on 2017-03-04
I tried /dev/sdb and and /dev/sdc as well but no luck

---

### Post by ubfan1 on 2017-03-05
Your Windows 10 is installed in UEFI mode, so you should install Ubuntu in UEFI mode also.  I see no Ubuntu bootloaders in the EFI partition of sda, so maybe you tried to install Ubuntu in  legacy mode, and your gpt disk partitioning does not have a 1-2M partition labeled grub-bios, so it failed.  Now it looks like you do have a grub installed to sdb, which is a dos partitioned disk.  Can you boot from sdb?

---

