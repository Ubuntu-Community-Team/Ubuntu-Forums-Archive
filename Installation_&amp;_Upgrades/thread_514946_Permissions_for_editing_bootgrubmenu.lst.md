---
title: "Permissions for editing boot/grub/menu.lst"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by acelin on 2007-08-01
How do I get the permissions for editing this? I want to change Ubuntu to boot to 0,1 instead of 1,1-

:guitar:

---

### Post by bulldog060 on 2007-08-01
user$ sudo -s
root# vi /boot/grub/menu.lst

user$sudo vi /boot/grub/menu.lst

---

### Post by merlinus on 2007-08-01
Or for graphical editing:

```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

### Post by acelin on 2007-08-01
Huh?

Please explain more:

I can get to it, but I cant sae it once I edit it because of my "permissions" supposedly.

---

### Post by forestpixie on 2007-08-01
in a terminal the command 

gksudo gedit /boot/grub/menu.lst

should do that

---

