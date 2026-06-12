---
title: "Grub Confused ??"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by railpostau on 2008-07-28
Have desktop comp P4 Celeron 2.4G, 2G DDR 400 Ram, 512 Nvidia 7200 vid card...

3 Hard Disks..

BIOS shows:

HD0 PATA 80G, partioned 50G Win XP, 20G Ubunutu (8.04), 800M Swap.

HD1 PATA 80G, partioned 3 equal NTFS

HD2 SATA 200G, partioned 3 equal NTFS.. SATA runs from a PCI card not directly from main board..

 Comp boots from HD0

On installing UBUNTU (no problems) until reboot.. Comp booted straight into XP..

Used UBUNTU as live disk and checked BOOT/GRUB config.. found that MENU 1st shows

UBUNTU 8.04 kernel at (hd1,4)

and

XP at (hd1,0)..

Question: Has Ubuntu counted the SATA HD as 0 and the rest sequentially..

If so how can I fix so that

1. UBUNTU boots from correct GRUB etc
2. Have UBUNTU boot from a USB key (for one very good reason)

Thank you for any help in this area

---

### Post by logos34 on 2008-07-28
During installation grub guessed the boot drive wrong...grub bootloader should be on the mbr of the other ide/pata drive.  Go into the Bios and set the hdd1 drive first in the hard disk boot priority.

---

### Post by railpostau on 2008-07-28
I cheated, opened the box, disconnected the other drives and re-installed UBUNTU..No problems..

Thanks for your help

---

