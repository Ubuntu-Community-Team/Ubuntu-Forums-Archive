---
title: "Boot Issue"
date: 2018-01-01
forum: Installation &amp; Upgrades
---

### Post by cmyamato on 2018-01-01
I installed Ubuntu alongside windows 10 and have no option to boot into it via grub or any other option. I opened the live client and ran the boot repair to no avail. Also, I did the recommended additional step of the windows cmd command to edit the bootmgr setting, but still nothing. Any help would be appreciated.
[https://paste.ubuntu.com/26302310](https://paste.ubuntu.com/26302310) is the log of it.
running on a Aspire R 15 laptop with all factory hardware, and an up to date bios.

---

### Post by ubfan1 on 2018-01-01
On Acers you need a few additional steps to run new bootloaders.  In the UEFI Settings (formerly known as BIOS) set a supervisor password, then set "trust" on the grubx64.efi and shimx64.efi.

---

### Post by cmyamato on 2018-01-01
Wow, worked like a charm thank you so much for the quick, and helpful reply!

---

