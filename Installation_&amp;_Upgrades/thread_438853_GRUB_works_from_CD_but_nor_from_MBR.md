---
title: "GRUB works from CD but nor from MBR"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by PascalWinnen on 2007-05-10
Hi folks

I have 2 identical SATA drives - number 1 in BIOS has XP on it, number 2 has Feisty on it.

In a first step I left the MBR of number 1 untouched. 
Without the super grub disk in the CD-rom, it booted XP problem-free without giving the option to boot Feisty. 
When I wanted to boot Feisty, I just booted with the super grub disk. Here I have the option to boot XP or Feisty. IMPORTANT: both OS boot perfectly with grub this way.

I've found it a bit a hassle to take the super grub disk in/out to boot, therefore I installed the working grub to the mbr of disk 1. Now when booting this gives me the same menu as with the Super Grub Disk and XP boots BUT Ubuntu doesn't:
ERROR 11: UNRECOGNIZED DEVICE STRING.

Strange, since this Grub config works fine when booted with the CD-ROM!

It also differs from the problems which other people encounter: in my case XP starts problem-free, it's Ubuntu that doesn't boot with Grub in the MBR of the XP drive.

Any ideas?

Thx,

P.

---

### Post by adrian15 on 2007-05-24
> **PascalWinnen said:**
> 
I've found it a bit a hassle to take the super grub disk in/out to boot, therefore I installed the working grub to the mbr of disk 1. Now when booting this gives me the same menu as with the Super Grub Disk and XP boots BUT Ubuntu doesn't:
ERROR 11: UNRECOGNIZED DEVICE STRING.
It also differs from the problems which other people encounter: in my case XP starts problem-free, it's Ubuntu that doesn't boot with Grub in the MBR of the XP drive.

Any ideas?


Can you copy-paste your menu.lst here so that we see where's the error ? (You can omit the lines that begin with a # ).

adrian15

---

