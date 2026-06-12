---
title: "Need to uninstall ubuntu"
date: 2020-06-14
forum: Installation &amp; Upgrades
---

### Post by suvrojit on 2020-06-14
I dual boot ubuntu with windows 10. For some reason I want to remove ubuntu and grub bootloader, I have attached a screenshot of my disk management screen from windows 10, looking at this, can anyone tell me which one is the partition ubuntu is installed on? I don't want to accidentally delete my data while removing ubuntu. I just hope it is not installed in C drive along with Windows.

[ATTACH=CONFIG]286215[/ATTACH]

---

### Post by CelticWarrior on 2020-06-14
Welcome.

The first partition is the ESP (EFI System Partition). Do not touch it!
Excluding this one then there are two non-NTFS partitions that should be from Ubuntu, likely / and swap.

Whatever you do make sure you have backups and although in UEFI systems one can do what you want without affecting the boot, you should have Windows installation media anyway, just in case.

The Grub in UEFI will remain, a bootloader that will no longer work to boot Ubuntu, obviously, but you can left that alone.

---

