---
title: "Trouble with guide on installing plop boot manager Ubuntu 14.04"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by alex191 on 2014-05-03
Im using this guide ([http://makegadgetswork.blogspot.com/2012/02/how-to-boot-from-usb-when-bios-does-not.html](http://makegadgetswork.blogspot.com/2012/02/how-to-boot-from-usb-when-bios-does-not.html)) to install Plop boot manager on my Sony Vaio and im getting this message

-PCG-V505BX-UC:~$ gksu nautilus /boot

(nautilus:4116): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))

---

### Post by RGMoonen on 2014-05-03
Put something like this into your /etc/grub.d/40_custom file:

robert@clevo:~$ cat /etc/grub.d/40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Plop Bootmanager" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7a7ae441-7197-4996-9aba-6c9cd0502ab9
	linux16 /boot/plpbt.bin
}

Making sure to use your own drives UUID.
Put plpbt.bin into the /boot directory, then run sudo update-grub and you will then have a plop boot manager entry in your grub menu.

cheers

Robert

---

### Post by tgalati4 on 2014-05-03
If the above doesn't work and your VIAO has a CD or DVD reader, then make a plop boot ISO CD and boot from that.  Then you can select your USB device after plop queries all devices.

---

### Post by bapoumba on 2014-05-03
I used that [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)
(Used it to boot on CD and then install from usb).

---

