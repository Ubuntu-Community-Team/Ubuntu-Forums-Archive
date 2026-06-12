---
title: "Problems with graphic card"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by anski on 2005-04-21
I installed the Ubuntu and it has been all ok, but when it tryes to start it stucks when open the desktop, I think it's for the graphic card, but I dont know. The computer is quite old and graphic card is Phoenix S3 TRIO 64 VGA. Is it incompatible? Should I try with another? or it isn't the reason.

Thanks for all

---

### Post by heimo on 2005-04-21
S3 based cards are very well supported, I think. I think that was the card in my first Linux machine - S3 Trio 64 with 512kB memory... Of course you can't do magical stuff or fancy 3D, but it's definitely supported. You must check that the driver selected for your Xorg is s3 or vga or vesa. You can reconfigure xorg on console using: sudo dpkg-reconfigure xserver-xorg

You can probably change to console even if your Xorg doesn't work. Try booting into recovery mode or hit ctrl+alt+F1 to get first virtual console. Login with your normal user account and use sudo to run commands which require root privilege.

Also pay attention to resolution and color depth. Try to get it working with something less demanding at first. For some hints how to tweak xorg.conf, check this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

Also you probably want to install xfce4 (lighter Window manager), instead of gnome.

This is nice guide for many Ubuntu tasks:
[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by anski on 2005-04-21
Thank you for replying, I tried to reconfigure for there, but I didnt succeed. Maybe I have to try more hard. Thanks!

---

### Post by heimo on 2005-04-21
You probably have quite limited graphics card memory, check this table for required memory for different resolution / color depths:
[http://www.physiol.ox.ac.uk/~trp/vidmem.html]("http://www.physiol.ox.ac.uk/%7Etrp/vidmem.html")

Also, if you attach your /etc/X11/xorg.conf and /var/log/Xorg.0.log and the output of command 'lspci', it'll give lots of information for us to help.

EDIT: Oh! And information about your monitor (make/model/resolutions) would also help.

---

### Post by anski on 2005-04-21
Thanks Heimo, it was all problem off the monitor and card configuration, I was trying to different options and now it is working ;).  And now start to work with Ubuntu!
Bye.

---

### Post by pelle.k on 2005-11-06
I've had this problem too. [THIS was my solution...]("http://www.ubuntuforums.org/showthread.php?p=471639")
Good luck

---

