---
title: "Keyboard doesn't work with Ubuntu installer"
date: 2019-08-03
forum: Installation &amp; Upgrades
---

### Post by ecec on 2019-08-03
When I boot from USB into a 64-bit Ubuntu 19.04 installer, the keyboard doesn't work. It works in the existing 32-bit Ubuntu 18.04 installation.

---

### Post by gdesilva on 2019-08-03
Are you using a bluetooth keyboard by any chance?

---

### Post by ecec on 2019-08-03
> **gdesilva said:**
> Are you using a bluetooth keyboard by any chance?
No, I'm using a USB keyboard.

Also, the keyboard light indicators for the lock keys light up, but pressing one of them has no effect. If I press any key on boot, the advanced welcome page appears and the keyboard works there.

---

### Post by ecec on 2019-08-03
Another update: Other keyboards work, it's just this specific keyboard which doesn't, although I prefer using it over the other keyboard I tried. When I plug in the keyboard an "Asus Management GUID not found" warning appears in the journal.

---

### Post by gdesilva on 2019-08-03
just to see what is going on I would try the following

1. boot the system with the keyboard that is working
2. run ' tail -f /var/log/syslog' on a terminal to monitor system messages
3. now plug in the usb keyboard that is causing the problem
4. you should get some messages when you plug in the second keyboard

This may give some idea what is going on.

Also check out the following link [https://askubuntu.com/questions/772056/keyboard-stops-working-ubuntu-16-04](https://askubuntu.com/questions/772056/keyboard-stops-working-ubuntu-16-04), in particular the post by FvD towards the end where he plugged in the keyboard through a powered USB hub and got the keyboard working.

---

