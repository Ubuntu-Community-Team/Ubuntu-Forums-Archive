---
title: "Install over Fedora with XP - Dual Boot Problem"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by sumgai on 2006-07-28
I had a dual boot system with WinXP and Fedora Core 5.0 (LVM) that ran pretty well.

I decided to install ubuntu 6.06 on top of the Fedora install (using same partitions, but reformatting them to ext3).

The install seemed to go fine and I installed GRUB on the MBR.

Now, when I try to boot, the system just says GRUB (after the BIOS post, etc.).  If I try to type, nothing is echoed.

I have 3 SATA disks on the system (AMD 4200/X2).  The second disk (sdb) has three partitions.  The main NTFS partition, an ext3 and a swap partition. (The other drives are all NTFS).

I tried reinstalling ubuntu, "repairing" XP with its automatic repair facility, but nothing is touching the boot record.

I obviously don't really get the boot thing too well and could really use some beginner-oriented help on this.

Many thanks in advance,

---

