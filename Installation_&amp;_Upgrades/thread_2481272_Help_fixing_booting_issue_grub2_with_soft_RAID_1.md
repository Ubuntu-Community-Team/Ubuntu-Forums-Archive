---
title: "Help fixing booting issue: grub2 with soft RAID 1"
date: 2022-11-23
forum: Installation &amp; Upgrades
---

### Post by greefea on 2022-11-23
Hi, I managed to brick my ubuntu 22.04 VPS and it no longer boots. I tried to boot into boot-repair ISO image via a KVM console. Oddly, boot-repair only has the option of Create Boot info Summary ([https://paste.ubuntu.com/p/YRcDqZYwBh/](https://paste.ubuntu.com/p/YRcDqZYwBh/)), but not the "Recommended Repair" button. Any recommendation how I may fix it? Thanks!

---

### Post by oldfred on 2022-11-24
Do not know RAID nor VPS.

But you booted Boot-Repair in UEFI mode and do have an ESP - efi system partition. But ESP is not mounted in fstab, so reinstall or update from inside system will not use UEFI.
You have grub installed to MBR, and have very old MBR (msdos) partitions.
So did you try to boot install in UEFI mode & it really is old BIOS/MBR? Check UEFI setting for default boot mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by greefea on 2022-11-24
Thanks for your response. I don't think I grasped what you described, as I am very new to the whole UEFI / GPT universe.  Reading srs5694's post, it seems MBR would work in my case (ubuntu only)? Can you give me a hint as of how I may get boot-repair to work for me? Or a step by step process how to fix my problem (I know this is a lot to ask; I have done quite a bit search myself, including in this forum, but I don't have any idea of the process). Thanks again!

---

### Post by oldfred on 2022-11-24
I do not know VPS and have never used RAID, do cannot really help.
I also have not used MBR since 2010 for any new drives or even larger flash drives.

A few still do use MBR and if you understand its limits it should work. Backup even more important.

Knowledgeable users here have suggest that if it takes more than an hour to repair, best to just reinstall & restore from backups.
But they all have data separate from system.

---

