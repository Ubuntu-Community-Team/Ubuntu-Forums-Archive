---
title: "[SOLVED] how to increse boot time"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by myharshdesigner on 2007-11-21
i want to increase boot louder time currently it's 10 or 15 sec max.

but i want to make it 25.


so any one can able to select Windows or Linux .

thanks
Harsh

---

### Post by Schalken on 2007-11-21
you need to edit the file /boot/grub/menu.lst as root. the command "gksu gedit /boot/grub/menu.lst" will open up the file for editing in gedit as root.

look for the line "timeout 10" (where 10 is whatever it is set to), and change it to "timeout 25" and save.

---

### Post by myharshdesigner on 2007-11-21
Thanks

---

