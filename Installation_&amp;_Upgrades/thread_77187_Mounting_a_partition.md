---
title: "Mounting a partition"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by jsmidt on 2005-10-16
I am trying to access my partition hda3 from a live cd since I messed up my boot files.  How do you mount a partition from a live cd?

---

### Post by aysiu on 2005-10-16
Is it a Windows partition? If so, [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by jsmidt on 2005-10-16
I'm sory I didn't explain myself adequitly.  I tried to install a splash screen to my grub bootlader trying to follow directions on gnome look.  When I restarted my computer grub wouldn't come up at all.  Someone suggested to reboot using a live cd.  I did but can't figure out how to access my /boot/grub/menu.lst to fix it.  It is in the hda2 partition.  How do I get to the file?

---

### Post by aysiu on 2005-10-16
```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda2 /ubuntu
sudo nano /ubuntu/boot/grub/menu.lst
``` This assumes, of course, that your Ubuntu installation is an ext3 filesystem. If you're unsure what type it is, type this in a terminal ```
sudo fdisk -l
```

---

### Post by jsmidt on 2005-10-16
Thank you so much aysiu.  It worked! :p

---

### Post by az on 2005-10-16
If you use grub, you can also modify the boot parameter on-the-fly.  Just hit escape if you are not shown the grub menu, pick the entry you want and hit "e" to edit it.

Enter and then "b" to boot.  You can change every line, if you want.  the changes are for that boot only, they are not permanent.

---

