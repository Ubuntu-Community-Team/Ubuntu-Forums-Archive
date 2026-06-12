---
title: "Dual Boot Dapper and Breezy"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-11-25
I want to dual boot Dapper and Breezy (multi-boot if you include WinXP).  Currently GRUB is installed on the MBR and is controlled by Breezy.

If I install Dapper, I think I have two choices.  Let Dapper overwrite the GRUB Install and hope that Breezy is picked up (or I can add it later) on the GRUB Menu (now controlled by Dapper?).  The second option is to tell Dapper not to install to GRUB and then add Dapper manually to the menu.lst  on my Breezy partition.

Which of the above scenarios is preferred (Breezy is my primary desktop,  I just want to fiddle with Dapper)?

Normally if I do a kernel upgrade (e.g. take Breezy to 686smp); the menu.lst is updated automatically by synaptic; everything is good!

However,  if I upgrade the kernel on Dapper (assumung Breezy controls GRUB) I assume I will have to reboot into Breezy and add the new kernel into the menu.lst?

Thanks

Mark

---

### Post by wjp.reg on 2005-11-25
Hi markr;

I have a similar installation and found that all my distros were found and setup automatically (SuSE, Dapper, Breezy).

Either way (auto or handwritten in menu.lst) should work fine :smile:

---

### Post by markr on 2005-11-25
What about if you upgrade the kernel on one of the distros, is that automatically added to GRUB or do you have to do it manually?

---

### Post by teaker1s on 2005-11-25
synaptic adds kernels to grub thats how I installed k7

---

