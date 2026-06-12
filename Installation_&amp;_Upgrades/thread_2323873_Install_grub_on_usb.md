---
title: "Install grub on usb"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by jimmyh1972 on 2016-05-09
I customized my system with squashfs, I deployed squashfs, vmlinuz,  initrd on a usb device and I want to boot using grub, I installed grub  on my usb but it didnt boot. how can I make a bootable usb?

---

### Post by oldfred on 2016-05-09
If you manually install grub, you have to manually create a grub.cfg to boot.

I normally install grub to flash drive and loopmount ISO.
While it says hard drive, it is the same for any drive. Just boot drive is always hd0, but partition and path may vary depending on your partitioning.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

