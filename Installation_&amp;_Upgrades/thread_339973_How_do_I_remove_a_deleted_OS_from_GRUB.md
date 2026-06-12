---
title: "How do I remove a deleted OS from GRUB?"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by lukon on 2007-01-16
How do I remove a deleted OS from GRUB?

My GRUB lists two instances of WIN98se because I did in fact have two instances at the time I installed ubuntu Dapper, and GRUB faithfully registered both.

Since then I have removed one of the instances of WIN98se. But GRUB still lists the deleted instance.

So again, can I remove the deleted WIN98se from GRUB? And if so, how?

---

### Post by mcduck on 2007-01-16
Press alt-f2 and run 'gksudo gedit /boot/grub/menu.lst'. Then just find the entry for your removed OS and remove it and save the file.

---

### Post by Sqwishy on 2007-01-16
i think if you click on ' system >> Administration >> boot ' that will give you a menu to change things, i think.
if that's not there you can open a term and look for grub.conf or something in /boot/grub/ ... i think that's where it is.
. . . or just listen to mcduck

---

### Post by lukon on 2007-01-16
Thanks folks.

I used the method proposed by mcduck and it seems to work just fine. Redundant WIN98 option gone.

---

