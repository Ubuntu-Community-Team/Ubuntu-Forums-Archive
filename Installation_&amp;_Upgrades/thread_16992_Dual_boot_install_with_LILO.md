---
title: "Dual boot install with LILO"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by MoeGreene on 2005-02-25
Hi,

I have a dual boot system with Windows 2000 and Debian Sid installed. The hard drive is partitioned into two NTFS partitions for Windows, and one EXT3 partition plus a swap partition for Debian. I use LILO as boot loader.

Now, I'd like to replace my Debian install with Ubuntu (Hoary possibly, or maybe I'll try Warty first). Will Ubuntu's installer make this an easy task or are there any possible pitfalls? What about LILO and GRUB? I understand that Ubuntu uses GRUB, will it automagically replace LILO or should I uninstall LILO before installing Ubuntu? I want to keep the Windows install as before.

I'm a bit unsure of the best way to do this to so any help is appreciated, TIA!

---

### Post by deBaas on 2005-02-25
It will do as you want. No problems. I had a dual boot with debian and winxp but replaces debian with ubuntu realy easy.

---

### Post by MoeGreene on 2005-02-26
So what you're saying is that Ubuntu's installer will remove all traces of LILO and replace it with GRUB? Sorry to be a bit anal about this but I'd hate to cause any problems to my system - I need to have my Windows install accesible.

---

