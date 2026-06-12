---
title: "Grub issue after each update"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by mathieumaes on 2007-12-24
I have a problem with my Ubuntu desktop which keeps recurring when an update has been done.

I have 2 harddrives: 1 SATA and 1 IDE. The OS is installed on the SATA one. The IDE one is used for data. Whenever the kernel is updated, it automatically regenerates the config file for grub namely /boot/grub/menu.lst as the following :

root            (hd1,0)

This is wrong! After each update I need to change it back manually to 0,0 in order to reboot properly.

Is there a way to avoid this going wrong every update ? The desktop is used as server without monitor, keyboard or mouse, so this problem keeps bugging me...

---

### Post by Pumalite on 2007-12-24
Change this to whatever is appropriate for you:
# kopt=root=/dev/sda1 ro
This other entry should look like this:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

---

### Post by *B* on 2007-12-24
> **Pumalite said:**
> Change this to whatever is appropriate for you:
# kopt=root=/dev/sda1 ro
This other entry should look like this:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

Would you please explain what this does, and if it prevents from having to rewrite the menu.lst file after each update. I have the same problem with a dual boot XP setup, and it was getting rather annoying knowing I had to rewrite config files every time I updated.

---

### Post by Pumalite on 2007-12-24
It prevents kernel upgrades from messing up your configuration.

---

