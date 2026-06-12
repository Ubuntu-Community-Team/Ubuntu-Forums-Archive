---
title: "Ubuntu Install on a USB HDD Drive with Vista + XP"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Xabora on 2008-01-29
Alright... I'm in a little pickle at the moment. 

Current my drive setup looks like such.

HDA0 - XP
HDA1 - Vista + Boot System
USB Drive - Blank


I want to install Ubuntu on the USB drive without effecting my Vista boot.
But so far I've found little to no documentation for this.


Would the best solution be to install it to the USB drive.. then fire up EasyBCD and assign an entry there?


/sigh my linux-fu has gotten rusty.

---

### Post by Pumalite on 2008-01-29
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Best to disconnect all internal drives during installation.

---

### Post by Xabora on 2008-01-29
Thanks,

I was hoping to avoid this but looks like I might have to do that.

---

### Post by Pumalite on 2008-01-29
Good luck!

---

### Post by Xabora on 2008-01-29
Ok one last thing.

With Grub, I keep on receiving a permission error each time the installer goes to install it on sda?

EDIT: I got it.

/dev/sda



Thanks for the help Pumalite. :D

---

### Post by Pumalite on 2008-01-29
You are welcome. Happy Ubuntuing!

---

