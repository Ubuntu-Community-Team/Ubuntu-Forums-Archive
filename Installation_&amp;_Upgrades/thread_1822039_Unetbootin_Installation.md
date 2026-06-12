---
title: "Unetbootin Installation"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by jcslzr on 2011-08-10
I installed Ubuntu with Unetbootin, when I boot I get a Unetbootin menu, that offers me to try or install ubuntu, but also the first option is "default"

Is this my installation? because i change a name folder and then i reboot and the folder had the original name so i suspect my changes are not getting recorded...how can i know if this is true or what can i do?

on the install options my usb (from where i am running ubuntu) does not show up

Thank you
Carlos

---

### Post by Hakunka-Matata on 2011-08-10
[LIST]
[*]The default option is the same as "try Ubuntu without installing it to hard disk"
[*]if you choose install, you can install it to your hard drive, you cannot install it to the USB, and you cannot write to the USB, the USB is READ ONLY.  It is used either to "try" Ubuntu out, or Install Ubuntu to your hard drive.
[/LIST]
You can however, create a USB with "persistence", which makes it a writable USB, that you can use as a portable OS and plug it into different computers, boot from it, and use is as if it were a hard disk.

Link to howto for persistence LiveCD -->  [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by beew on 2011-08-10
> **jcslzr said:**
> 
Is this my installation? because i change a name folder and then i reboot and the folder had the original name so i suspect my changes are not getting recorded...how can i know if this is true or what can i do?



All changes in the live usb are erased on reboot. If you want a live usb which allows you to save settings and data you need to create one with persistence. Unetbootin doesn't support persistence. You should use Ubuntu's Startup Disk Creator instead if you already have a Ubuntu install. If you are on Windows you can make a persistent Ubuntu usb with LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by beew on 2011-08-10
> **Hakunka-Matata said:**
> 
Link to howto for persistence LiveCD -->  [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Dude, that is not very helpful. Presumably new users are most interested in making live usb with persistence to test the water and this guide is just ridiculous. There are many GUI tools in Linux as well as Windows that can do the job without having to go through a bunch of gibberish like that (and I don't find cutting and pasting commands that one doesn't understand an educational experience so it is being obscure for no good reason)

---

### Post by Hakunka-Matata on 2011-08-10
I found the [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) link helpful and interesting.  Different people learn things in different ways.

---

