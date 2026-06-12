---
title: "corrupted boot_loader"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by mrpossible on 2020-05-08
[https://paste.ubuntu.com/p/shVZqh2Nd4/](https://paste.ubuntu.com/p/shVZqh2Nd4/)

Hi, I'm new and don't know what happened but my machine cannot boot now, I messed around with the boot loader, now I'm confused and don't know what to do next. Please help! I tried with Boot Repair tool and get this link, but don't know how to interpret those. This happens while I'm updating my Ubuntu from 18.04 to 20.04.

---

### Post by oldfred on 2020-05-08
It looks like you have UEFI system with newer NVMe drive.
And have Ubuntu installed in UEFI boot mode, but had installed a BIOS boot version of grub into the gpt partitioned drive's protective MBR for BIOS boot.

Be sure system is set to only boot in UEFI mode. If it tries to boot in BIOS/CSM/Legacy mode, it will find grub and try to boot, but fail. 

Only use Boot-Repair in Ubuntu's live installer booted in UEFI mode by using ppa to add it.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If it still does not boot, try Boot-Repair's advanced mode when Ubuntu live installer booted in UEFI mode, choose install, choose drive and also check install latest kernel and full reinstall of grub.
Since not otherwise used the grub in the MBR is not an issue as long as you do not try to use it.

---

