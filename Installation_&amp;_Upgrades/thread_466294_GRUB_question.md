---
title: "GRUB question"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Ryan Sullivan on 2007-06-06
I really need to know: Iif i install ubuntu and don't install the GRUB to the MBR or bootsector, in theory Ubuntu boots up automaticly after installation, but, if i do a FIXMBR o FIXBOOT would i get the windows boot loader again???

I need to know because i don't want to touch the MBR and i was thinking of using a supergrub disk.


Thank you

---

### Post by logos34 on 2007-06-06
Then specify during install for grub to go on your root partition--e.g. '(hd0,0)' or '/dev/hda1', not '(hd0)' or '/dev/hda)'--send it to a floppy (fd0) or even a /boot partition (if you created one)

Fixmbr will overwrite anything on the mbr with the windows bootloader.

---

