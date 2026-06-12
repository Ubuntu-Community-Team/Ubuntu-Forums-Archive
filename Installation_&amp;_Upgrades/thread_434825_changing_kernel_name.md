---
title: "changing kernel name"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by jhewer on 2007-05-06
hello,

i recently compiled and installed the 2.6.21.1 kernel, but i was wondering whether it's possible to change the name of the kernel once it's installed, or if not change the name of the kernel with the deb's i created?

there's no particular reason why i want to do this, other than to make the kernel name a bit nicer :)

thanks
jon

---

### Post by alenis on 2007-05-06
If you mean chaniging the name in the Grub menu, just edit /boot/grub/menu.lst

---

### Post by jhewer on 2007-05-07
i meant changing the local name / the bit which is appended to the actual version.  i stupidly appended 2.6.21.1 so it's 2.6.21.1-2.6.21.1 everywhere, not just the name in the grub menu.

if it's easy to change the bit after the '-' everywhere.  like i said, there's no particular reason why i NEED to do this, i would just like to if it's not difficult

thanks

---

### Post by jhewer on 2007-05-07
alternatively if it's possible to change this detail in the .deb files for the linux-image and linux-headers that would be good to know.  i would have thought it would be possible to do this, otherwise if someone wanted to change it then they'd have to recompile.

cheers

---

