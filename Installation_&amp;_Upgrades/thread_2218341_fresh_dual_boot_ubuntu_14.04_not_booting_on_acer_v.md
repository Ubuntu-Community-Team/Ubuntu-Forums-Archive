---
title: "fresh dual boot ubuntu 14.04 not booting on acer v5 561g with windows 8.1"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by 2 legit 2 quit on 2014-04-20
I have installed ubuntu 14.04 as a dual boot using a live usb on an acer v5 561g with an intel i5 processor and I cant boot into ubuntu at restart. It seems that the grub2 bootloader is broken. I tried using boot repair with no success. 

I need help to figure out how to fix this problem.

Here is a link to the boot info file generated: [http://paste.Ubuntu.com/7286539/](http://paste.Ubuntu.com/7286539/)

---

### Post by oldfred on 2014-04-20
The grub repair reported an issue. And some of it is inconsistent.

       Wrong GRUB version detected.

Installation finished. No error reported.
An error occurred during the repair.

I have seen others with the Wrong version but it still worked so not sure if Boot-Repair or grub is reporting something that is not.

Can you boot ubuntu entry in UEFI? 
If then Boot-Repair offers 'buggy' UEFI do not say yes. Only those systems that only boot Windows need that fix.

Have you tried booting with secure boot off? It looks like you have the secure boot kernels installed, but also have standard UEFI kernels also. 

And it looks like you originally installed in BIOS boot mode as you have grub in the protective MBR for BIOS boot. But either reinstalled or Boot-Repair converted you to UEFI boot. Be sure to always boot in UEFI mode.

If still not working I would try the full uninstall and reinstall grub in advanced options. Be sure to be booted in UEFI mode.

---

### Post by 2 legit 2 quit on 2014-04-20
Thanks for the information. I switched secure boot off and finally got it booted into ubuntu 14.04.

Thanks again oldFred

---

