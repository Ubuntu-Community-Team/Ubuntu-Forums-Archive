---
title: "External Hard Drive And Linux"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by .fred on 2007-12-11
Hi Linuxes! :lolflag:

I installed Ubuntu 7.10 on my external HDD and everything went well. However, when i rebooted and took out the disc, i got a shock:

GRUB or something worked well, showed me that i could load Ubuntu 7.10, Ubuntu 7.10 Recovery Mode, MemTest, and under other versions, showed Win XP.

So i scrolled and highlighted the first option, but a panel of errors about not being able to allocate resources 7 8 and 9. Then it said kernel panic-not syncing, and said the hd was wrong, i think. With this message: "Unable to mount root fs on unknown-block(0,0)". 

Since this is on my External HDD, and my main HDD has two partitions, and my external has 3 partitions, under edit, should the root be (hd 1,0) since it is the second HD and the first partition?

Or is it a problem with the installation? 

Could someone help me?

---

### Post by logos34 on 2007-12-12
where is grub--are you booting from the usb or internal hard disk?  If the former, the 'root' line should read (hd0,0).  If the latter, (hd1,0).  What is odd is that menu.lst is coming up on the grub screen with a list of the OS's, which means it can find the root partition (/boot/grub/menu.lst), but it's freaking out trying to load the kernel image.  Might have to pass some kernel parameters/boot options 

Your Bios does support usb boot, right?

---

