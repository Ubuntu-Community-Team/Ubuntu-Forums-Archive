---
title: "Install ubuntu in an external hdd"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by d4n1el on 2005-09-04
HI!
My problem is that im stuck with a computer that only runs Win Xp.. and  i am not used to it and would rather run linux =)
I got an externel usb harddrive, and thougt to install linux. ubuntu in that.. 
But my question is, is it possible to instead of choosing os in grub, use bios to choose which hdd to boot from? Becuase i want to be 100 % sure that win will boot up normally when i leave this place..

---

### Post by d4n1el on 2005-09-05
dump.. 
anyone who know what to  do? or do i miss something that i need to explain?

---

### Post by lol on 2005-09-05
[QUOTE=][/QUOTE]
 I don't know whether or not it's possible to install linux on a usb drive, but assuming it's possible, I would install grub anyway, on the windows HD.

I used to do this when my linux was installed on a removable rack. You can install grub on the HD you want, using : grub-install --root-directory=DIR

Another solution would be to use a bootable grub floppy.

---

