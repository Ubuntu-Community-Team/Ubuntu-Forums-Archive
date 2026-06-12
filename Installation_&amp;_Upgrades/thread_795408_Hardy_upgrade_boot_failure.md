---
title: "Hardy upgrade boot failure"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by nspur on 2008-05-15
I had Gutsy installed with Wubi. Worked great. Today I upgraded to Hardy which seemed to go well but on booting I get

find --set-root --ignore-floppies /boot/grub/menu.1st

Error 17 : File not found

I'm not really Ubuntu-literate. Is there anything I can do about this? Other than install from scratch.

Help much appreciated 

-EDIT-
I've found the path to the menu.lst file. It's on the Windows C drive in ubuntu\disks\boot\grub along with a file device.map that points at the primary Windows partition.

Thanks

Nick

---

### Post by hermes0710 on 2008-05-16
Before pressing enter in the grub menu can you press 'e' when the ubuntu entry is selected and post here what it shows?

---

