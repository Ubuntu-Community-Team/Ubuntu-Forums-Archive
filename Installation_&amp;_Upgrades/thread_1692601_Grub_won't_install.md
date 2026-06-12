---
title: "Grub won't install"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Pizarro on 2011-02-21
Trying to install on a machine with xp on it and it fails with error "sorry, an error occurred and it was not possible to install the bootloader at the specified location." I've installed many times as single and dual boot on several machines (even with this disk)but never had this problem before. I have tried all the options on the drop down menu to no avail.

---

### Post by gufide on 2011-02-21
did you go on specify partition? You must select ext4 and put a "/" for mount point to get ubuntu install correctly

---

### Post by Pizarro on 2011-02-21
I've formatted whole drive and re-installed again. Have installed grub via terminal using these commands
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda 

If I reboot I get a grub screen but I assume something eg menu.lst is missing from the boot/grub. I have no idea where to go from here. I thinl I must create an entry or something from a live cd boot.

---

### Post by Pizarro on 2011-02-22
Sorted it. Installed grub as I said and cured the problem by downloading and booting with rescatux. I think that this would have installed grub as well but I'd already done it. Just run the rescue option and rebooted system after accepting the defaults and ubuntu booted.

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

