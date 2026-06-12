---
title: "Flashing purple screen - ubuntu 10.04 laptop install"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by linux_usr_crm on 2010-06-01
Hi,

I am attempting to install Ubuntu 10.04 (32 bit desktop edition) on my Asus X58c laptop, 1.2GHz, 2GB ram, SIS 671/771 integrated graphics.

After booting the CD and selecting language I get a rapidly flashing purple screen with horizontal lines flicking across it.

If I reboot and use F6 and add vga=771 at the end of the kernel options as the help screen suggests, the screen appears normally and I am able to install successfully, but upon rebooting into the freshly installed system I have the same problem again with the flashing purple screen, and am unable to see if the machine is booting.  There is disk activity, but because of the screen problem I have to do an emergency restart.

I have tried using the 'e' option in the grub menu and adding vga=771 or nomodeset at the end of the kernel options but to no avail.

I recall a similar problem on an earlier version of ubuntu where it was necessary to disable the framebuffer but this does not appear to be an option with 10.04.

I have also tried using the alternate install CD, but this doesn't even recognise the vga=771 parameter.

If anyone has a fix or workaround for this I would be pleased to hear about it.

Regards

---

