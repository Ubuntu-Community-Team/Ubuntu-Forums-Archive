---
title: "Edit boot config"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Magoo69 on 2006-06-05
OK, apparently I need to add the parameter or "pci=conf1" in my boot loader configuration file? 

How do I do this?

This is to get my onboard video working.  :-)  :-)

---

### Post by localzuk on 2006-06-05
The file is /boot/grub/menu.list (IIRC).

Edit this by running 'sudo gedit /boot/grub/menu.list' on a console/terminal.

The kernel listings are normally at the bottom of the file

---

