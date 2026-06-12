---
title: "Kubuntu 6.10 on USB HDD - not booting"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by inductor on 2006-12-18
Hi all.

I`ve installed Kubuntu on my external HDD. It booted on my home PC, and I had no troubles until I tried to boot Linux on the PC at work. Well, the first problem was the drive letter changed from sda to sdb. I pointed grub to the right location, and now the kernel boots up, launches initrd (or initramfs, don`t remember) and reports USB module errors. It seems it doesn`t see the USB HDD. Should I rebuild initramfs image? How to do that? What modules to include?

Thanks in advance, and sorry for my poor English.

---

### Post by gn2 on 2006-12-18
Is the work PC the same model as the home PC ?

If not, the drivers will be different......

---

### Post by inductor on 2006-12-19
No, they are different. However, I tried two other computers  - on them Linux boots without a problem. AFAIK, drivers for the most common motherboards are already in the kernel, so my motherboard seems to be the problem. I`ll try to upgrade BIOS.

---

