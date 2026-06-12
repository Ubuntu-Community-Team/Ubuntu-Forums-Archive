---
title: "Grub  rescue"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by alex4592 on 2019-04-13
I installed ubuntu for first time all good with install but when he asked me to restart my PC I did it and i got error file  grub/boot/i386-pc/normal.mod not found  I need help...

---

### Post by oldfred on 2019-04-13
That error is typical of a grub mismatch.
Often old grub in MBR, and new install is UEFI, and UEFI/BIOS set to boot from MBR. Or vice-versa.
Or old grub in MBR, and you installed new grub to PBR, partition boot sector. BIOS only boots from MBR.

What brand/model system?
UEFI or BIOS install?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

