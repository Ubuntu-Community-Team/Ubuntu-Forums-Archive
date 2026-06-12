---
title: "Can't install grub to the install partition"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by benali72 on 2010-08-06
Hi,

I'm trying to install Lubuntu to /dev/sda6.

The computer already has another Linux on it along with Grub.

In the Advanced tab just prior to the Lubuntu install, it will let me install Grub to any partition EXCEPT /dev/sda6.

Am I doing something wrong?  /dev/sda6 is where I want to install Grub since the MBR is already covered by the previous Linux on this computer. I need to install Grub to /dev/sda6 so that the new Lubuntu install is bootable.

Thank you.

-------------------- [SOLVED] -------------------------

I just went ahead and installed Lubuntu anyway, without installing Grub (I un-checked the option to install Grub in the ADVANCED tab).

Then after the Lubuntu install, I just went to the Linux that had the menu.lst and updated it to include boot info for the new Lubuntu install.

Works fine.

What threw me was that in other Linuxes, you check to install Grub into the new Linux's partition. With Lubuntu, you don't have to do that.

qed!

BTW... Congrats the Lubuntu team for a job very well done.  Great system!

---

