---
title: "Dual Booting using 2 Harddrives"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by maprx on 2007-03-24
I want to put Ubuntu on drive 1 and PCLOS on the other.  The boot record is always written over by the other distro?  How can I get the grub or lilo to see the other distro.  I know if I load Xandros, it finds all other distros?

Thanks

---

### Post by 1/0 on 2007-03-24
OK this is a guide for Windoze XP but it should be applicable for other OS:s.

[http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)

Otherwise this one might help:

[http://www.pclinuxonline.com/wiki/GrubMenu](http://www.pclinuxonline.com/wiki/GrubMenu)

---

### Post by bulldog on 2007-03-24
You can add it manually after you installed both OS's in your menu.lst [if you're using GRUB]

```
gksudo gedit /boot/grub/menu.lst
``` make a copy of your menu.lst before you change anything,just to be on the safe side```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by 1/0 on 2007-03-26
Did it work?

---

### Post by enopepsoo on 2007-03-26
I always just take the old menu.list entries from the first OS installed and copy them into the active menu.lst, then you know you have not made a mistake.

---

