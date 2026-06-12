---
title: "Installing on Adaptec 1200A (hpt370 chipset)"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by IvoE on 2005-03-30
As described in the title, I have a computer with a Adaptec 1200A controller with 2 WD 120Gb HD's in a raid 1 config. The chipset used on this controller is the hpt370.

When I start the installation, the harddisks are recognized as 2 separate HD's and not as a single raid device, caused by a kernel without the hpt370 module.

Is there someone who can provide me a module, which I can load from a floppy during installation, so I can install Ubuntu on the raid device?

---

### Post by IvoE on 2005-04-26
I've still got problems with installing ubuntu on raid 1 configurations. Now I have another machine with an other raid chipset. We have 5 of these machine's in total and 4 of them are running a plain debian installation. I have created some bootdisks in the past with a custom created kernel with ataraid and pdc202xx support. Those 4 machines are running debian on a hardware raid 1 configuration now, bootloader is grub.

This means it is support by linux, but when I try to do a ubuntu server install on this 5th machine the raid controller is nog recognized and I'm not able to install ubuntu on a raid device.

Is there some manual about how to create a custom installation disk (or cd) with a customized kernel which is supporting ataraid (pdc202xx is allready supported, but I'm not sure if it's with raid 1 support)

---

### Post by CIRANO2 on 2005-07-12
:razz: can help me find the uptodate driver for win xp-sp2?
thanks

---

