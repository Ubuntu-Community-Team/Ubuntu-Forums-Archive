---
title: "ubuntu server on usb, moving to internal hd"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by stairwayoflight on 2008-06-11
Hello,

I have installed Ubuntu 8.04 Server onto an external drive, and I want to move it to an internal drive. The reason is I don't want gnome/kde/xfce, and I am installing to an eeepc with no optical drive. What is the best way to do this? I am thinking of:

1. boot a live usb linux from a flash drive
2. copying from usb hard drive to internal ssd via "cp -r /mnt/usb/* /mnt/ssd/"
3. changing /etc/fstab and /boot/grub/menu.lst as necessary

Is there anything else I have to watch out for?

---

### Post by ashleycameron on 2008-07-08
your procedure is correct for transferring form usb to hd.
But make sure you are not connected to any network.

---

### Post by upchucky on 2008-07-08
partimage can create iso image of the ubuntu and save to a storage drive, then restore the image to any partition you want, then edit grub to tell it where you put the restore

---

