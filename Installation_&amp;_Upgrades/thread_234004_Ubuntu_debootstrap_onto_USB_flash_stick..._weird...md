---
title: "Ubuntu debootstrap onto USB flash stick... weird..."
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by jafa on 2006-08-10
Hi guys,

I am trying to get a machine to boot Ubuntu (core) from a USB flash stick. The flash stick is treated as a hard drive by the bios.

First test - single sata drive (sda) installed in machine. I booted from Ubuntu CD in rescue mode and ran debootstrap. Installed kernel and grub... reboot machine... it boots ok and everything works.

I removed the sata drive and installed the flash memory stick - still /dev/sda. Repeat the exact same steps except the flash doesn't have a swap partition. The root partition is ext3 - same as the sata hard drive.

Problem #1: Grub reports "error 17" and stops (ie no grub menu).

If I have the Ubuntu install CD in the CD drive and choose the boot option "boot from first hard drive" then grub boots to the menu ok. Weird.

Problem #2: Grub locks up when attempting the "savedefault" operation.

I avoided this problem by removing the savedefault command :cool: 

Problem #3: Keyboard.

The keyboard works ok when navigating the GRUB menus, however 9 times ot of 10 the machine loses the keyboard somewhere in the processs of booting linux. I get a login prompt and the keyboard is dead. Not even capslock or Ctrl-Alt-Del work.

A login prompt... this feels so close to working :D

Any ideas of how to figure this one out?

Thanks,

Nick

---

