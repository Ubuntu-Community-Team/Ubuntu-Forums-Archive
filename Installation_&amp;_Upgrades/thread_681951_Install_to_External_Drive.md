---
title: "Install to External Drive"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by crazy8 on 2008-01-29
Im sure this may have been asked in multiple forms, a million times but I cant seem to find anything that will help with the issue im having. I have an external WD 160GB hard drive that I would like to install Ubuntu onto. When I do I can never get it to boot. My laptop does support booting to a USB drive and I dont have an issue booting to my thumbdrive. Anyway does anyone have any input or know of any tutorials on how I can install the newest version of Ubuntu onto my USB hard drive?

Thanks alot for all the help.

---

### Post by Pumalite on 2008-01-29
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by crazy8 on 2008-01-29
I must be doing somethign wrong.
Right now I get an ERROR 17 when I install it and try to boot to my external drive. Here is what I am doing (this is how I have always installed linux)

Create partitions-
/boot - 100 
swap - 1024
/        - 40GB

Install OS
Grub on /dev/sdb (my partitions if i recall were sdb1,sdb2, and sdb3)

Once everything is installed and it restarts i take out the CD and let my system boot to the external hard drive and I select the Ubuntu Server and I get the ERROR 17.

would it make any difference if I tried Ubuntu Desktop for my laptop?
Any Ideas?
Thanks Again

---

### Post by Pumalite on 2008-01-29
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Probably Grub got installed half in your internal drive and half in your external drive.
Are you able too boot Windows with your external disconnected?

---

### Post by crazy8 on 2008-01-29
yes I am able to boot to my windows when i have the external unpluged.

---

### Post by Pumalite on 2008-01-29
Have you changed the boot order in BIOS to boot from USB first?

---

### Post by Pumalite on 2008-01-29
Sorry. Obviously you are booting from USB. Therefore the error message. Follow the link I gave you previously. See if you can fix it. Otherwise; reinstall.

---

