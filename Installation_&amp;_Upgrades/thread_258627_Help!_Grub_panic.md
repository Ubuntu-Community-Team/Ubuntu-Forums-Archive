---
title: "Help! Grub panic"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by tricky76 on 2006-09-16
....

---

### Post by tagra123 on 2006-09-16
Since your system is able to start grub its usually just a matter of pointing to the right partition and image.


Here is a how to for Grub
[https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1](https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1)


Also

To prevent this in the future:

Before editing the menu.lst make a backup.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak.SOMEDATE

By making the backup -- if your system will not reboot -- you can insert the live cd and mount the harddrive partition containing the root filesystem.

After its mounted then you can simply copy the backup copy to the original filename and the system should work just like before.


sudo cp  /boot/grub/menu.lst.bak.SOMEDATE /boot/grub/menu.lst

Reboot the computer.

I keep a printout, in the desk, of /etc/fstab and /boot/grub/menu.lst for just this sort of problem.

---

### Post by tricky76 on 2006-09-16
...

---

