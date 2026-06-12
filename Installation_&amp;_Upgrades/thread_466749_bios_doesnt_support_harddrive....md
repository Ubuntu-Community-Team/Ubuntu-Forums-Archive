---
title: "bios doesnt support harddrive..."
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by blaze92 on 2007-06-07
I'm trying to install ubuntu Server Edition on a compaq PII 350 deskpro. The problem is that the computer is pretty old and the bios doesnt support the 80gb hard drive. I've been told by my linux geek friend that i need to make a 200mb boot partition, however I've tryed that and cant seem to get it running. When i try to boot linux it says...

GRUB Loading stage1.5.

GRUB Loading, please wait

Then it just stops there, how exactly do i get it to work?
btw im new to linux....

Thanks
Blaze92

---

### Post by logos34 on 2007-06-07
Maybe grub Stage1 is still pointing to the root rather than /boot partition.  Also, /boot has to be at the front of the disk/first partition, within the 1024 cylinder limit (I'm guessing that's the issue here), otherwise it'll be out of range and it will be unable to load the grub menu.

---

