---
title: "Boot Live CD as NOT live CD"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by richiesgr on 2007-10-02
Hi,

I've installed the live CD (7.10) on Stick USB following the very good tutorial found in this forum.

But I would like to use it as normal install not live CD to use the usb has hard drive

Can I make this or do I need to install on the stick another image ?
If another image wich one ?

Thanks

---

### Post by 505 on 2007-10-02
I don't know which guide you've followed, but most guide use a 1GB USB stick. 700MB for the installation, and the other 300MB to save settings and files. This partition should be writable and containt the /home folder. After that is the case, just change the boot order.

---

### Post by richiesgr on 2007-10-02
Hello

I've already 2 partition but when I boot I see only boot as live CD not normal boot.
 do I need to add the option in lilo ?

In other word my question is how can boot live CD as normal installation ?

thanks

---

### Post by picopir8 on 2007-10-03
A little hack I have used....

You should see a .cfg file containing all the boot options for the live cd.  Edit the file and make sure the default points the the option that you wish to boot, then change the timer from 300 to 1.

---

### Post by richiesgr on 2007-10-03
Cool 
but wich cfg have you changed ?

---

### Post by picopir8 on 2007-10-08
I think its isolinux.cfg, IIRC.   Just make sure the default is set to the item option you want to boot and then set the timer from 300 (which is the 30 second timer x10) to 1 (so it boots that option within 1/10 of a second which is pretty much right away).

---

### Post by evets on 2007-10-09
I use the Live CD all the time to move files from one machine to another. After it boots up, there is an "Install" icon on the desktop. Clicking this will start the installation process.

---

### Post by Cryptog on 2007-10-09
I'm using Ubuntu on a USB drive, but installed it like a hard drive, without a compressed CD image. I used the livecd to install it. It is taking about 3.3GB of space on a 4GB usb flash drive.

---

