---
title: "Windows Boot Loader and GRUB?"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by ojdon on 2011-06-14
Hi there, I installed Ubuntu 11.04 64-Bit via Wubi but it seems that when I turn on my machine I first get the Windows Boot Loader, when I select Ubuntu from the list it then goes into GRUB with the option to select Ubuntu or Windows. 

Is there any way to change this so only GRUB is used? 

Thanks!

---

### Post by mastablasta on 2011-06-14
i think maybe you installed it wrong. there should be only windows boot loader as wubi actually sticks all the operating system inside a large file that is actually running in sort of virtualization inside windows. it's separated but it's not at the same time.

---

### Post by ojdon on 2011-06-14
I might just stick with the Windows Boot Loader then, everything works fine it was just an annoyance. I'll just set the time out in grub to 0. If anyone does have a possible solution then fire away!

---

### Post by Rubi1200 on 2011-06-14
I would recommend that you don't change any settings. Wubi uses the Windows bootloader and what you are seeing is normal, even if slightly annoying.

---

