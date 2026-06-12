---
title: "GRUB Command  Myth's"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by stumay on 2010-06-15
Please follow these instructions grabbed from this link:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

If you need to get into the grub menu to modify boot options or choose a  different kernel, you need to press 'ESC' just after it starts.

 By default you have to press  'ESC' within three seconds. If you want to increase this time limit, you  can edit the grub configuration file /boot/grub/**menu.lst**,  increasing the seconds in the TIMEOUT part.

Alternatively you could have the menu always come up at boot time.  To  do this, comment out 'hiddenmenu' by inserting a # at the beginning of  the line.

Thank you for finding this Stu! :guitar:

---

