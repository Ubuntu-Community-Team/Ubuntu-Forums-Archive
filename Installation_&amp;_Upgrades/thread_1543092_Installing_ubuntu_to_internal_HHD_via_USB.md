---
title: "Installing ubuntu to internal HHD via USB"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Linuxar on 2010-07-31
Hi I have a bit of a problem. I downloaded the Ubuntu .iso and burnt it on to a CD. It boots fine on all systems apart from the one Im trying to install it on.

This laptop dosent have a floppy disc drive or the option to boot from a USB pen drive.

I've taken the Hard disk out of it and used a USB drive caddy to connect it as a USB drive on a system running XP.

How do I go about Installing Ubuntu onto the this USB drive so I can put it back in the laptop as an internal HDD.

I've tried unetbootin to install the iso to the USB HDD but when I put it in the laptop as internal drive it dosent boot.

Can anyone help please?

---

### Post by gordintoronto on 2010-07-31
Boot from the LiveCD, and choose "install." During installation, you will be asked where to install it to. It almost certainly won't be the default location, there will be a drop-down list showing something like "SDA" and you want to change it to "SDB". (Or maybe HDA and HDB.)

---

### Post by C.S.Cameron on 2010-07-31
Just make sure that after partitioning you select Advanced and install grub to the laptop drive.
It might be wise to disable the Windows drive before installing or at least do an update-grub once the HDD is back in the laptop to get rid of the mention of Windows drive in the grub.cfg file.

---

