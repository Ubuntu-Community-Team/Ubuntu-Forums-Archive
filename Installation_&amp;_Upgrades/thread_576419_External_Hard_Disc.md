---
title: "External Hard Disc"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by helliewm on 2007-10-15
I have bought an External Hard Disc which shows its mounted in Ubuntu and I want to put Sabyayon on it. I have been into Bios and I cannot seem to boot into the external hard disc. Does anyone know how to get Sabaynon on it?

Helen

---

### Post by celettu on 2007-10-15
The same way you install any other OS? :) Sabayon is a Live DVD, just boot it up and install it on the external HD.

You'll have to pay attention to the bootloader settings, of course. Don't let it overwrite your MBR.

---

### Post by helliewm on 2007-10-15
I can't find the external hard disc in the Boot LOader settings. Also I am using Grub as I am 100% Ubuntu.

Helen

---

### Post by celettu on 2007-10-15
Well, obviously you can't boot into the external HD if there's no OS on it.

If you have installed Sabayon on the external HD already, you'll have to edit /boot/grub/menu.lst and add a Sabayon entry.

I can't be more precise since I'm not in front of your PC, but what I always do when I install a second OS, is to install grub on the same partition/HD the OS is on, then boot back into Ubuntu, open the menu.lst files on both partitions, and copy/paste the relevant entry to menu.lst on my Ubuntu partition.

HTH

---

### Post by helliewm on 2007-10-15
Thanks will give this a go.

Hrelen

---

### Post by logos34 on 2007-10-15
Here's a guide that you may find helpful:

[http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/](http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/)

It's for Feisty but it should work for sabayon too (although menu.lst may be called grub.cfg).  Skip steps 8-11 and remember to install grub on the external drive MBR so it doesn't overwrite the internal. Then like celettu says add a sabayon entry to your ubuntu menu.lst.  

> I have been into Bios and I cannot seem to boot into the external hard disc.

If you don't see the external usb listed in the hard disk boot priority then it may be that your computer/Bios does not support booting form usb.  In which case you can try [this workaround.]("https://help.ubuntu.com/community/BootFromUSB")

---

### Post by helliewm on 2007-10-15
Thanks the work round from Ubuntu is what I needed.

Helen

---

