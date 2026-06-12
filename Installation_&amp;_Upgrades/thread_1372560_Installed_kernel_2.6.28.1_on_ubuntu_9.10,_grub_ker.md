---
title: "Installed kernel 2.6.28.1 on ubuntu 9.10, grub kernel load error"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by theegyptianwarrior on 2010-01-04
Over the past few days I have been trying to install an older kernel (kernel 2.6.28.1) on ubuntu 9.10 64-bit WUBI installation. I compiled, installed, and updated my grub for the kernel. When I reboot, the grub menu correctly gives me the option of booting into the older kernel but when I do so I receive the following error message:

error: you need to load the linux kernel first.

I am at a complete loss on how to fix this. I even downgraded grub but I still get the same error.

Anyone know how to fix this?

---

### Post by theegyptianwarrior on 2010-01-05
Any one?

---

### Post by indian_gamer2003 on 2010-01-12
I googled this same error and got the solution. 

Run **sudo update-grub** and everything should work fine. If that doesnt work, move all the files ending with **-28-generic** from **/boot/** into a temporary folder and copy them back to their original location and try the above command with an additional **sudo grub-install /dev/sda**.

If you get an error for the second command, ignore it and reboot your system and everything should be fine.

---

