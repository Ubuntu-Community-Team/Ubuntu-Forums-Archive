---
title: "GRUB - Menu.lst"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by asad78611 on 2007-10-28
I have just installed Xubuntu 7.10 (Gusty Gibbon). After going through the installation I chose not to overwrite my existing bootloader. I already am able to boot to GRUB through the GRUB4DOS package.

Xubuntu has not updated the settings in the menu.lst

Therefore I am not able to boot into Xubuntu.

I need the settings to add to my menu.lst file

The hard disk is (hd0,6)
I believe the kernel is /vmlinuz
I am not sure bout the initrd.

Any chance I could get the details to add into the menu.lst

Or a way for Xubuntu to add its own details to an existing menu.lst without chaining the existing bootloader

---

### Post by taurus on 2007-10-28
You need to know the exact kernel name (and initrd) as well to add those two lines to /boot/grub/menu.lst.

Can you boot from the LiveCD and look at the content of your harddrive, mounting it first, of course?

---

### Post by logos34 on 2007-10-28
run

**sudo update-grub**

(i.e. from the live cd, with root mounted)

CORRECTION: 
I was wrong, can't run update-grub from live cd (unless there's a way involving chrooting)...I guess I was thinking of 'grub-install' which CAN be run from live cd

---

