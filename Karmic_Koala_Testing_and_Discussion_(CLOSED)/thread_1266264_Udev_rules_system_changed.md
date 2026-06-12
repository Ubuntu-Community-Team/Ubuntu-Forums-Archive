---
title: "Udev rules system changed ?"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popeye on 2009-09-14
Hi all,

I tried to get the Brother DCP-8060 printer/scanner to work. The printer works fine, however the scanner needs some extensive setup. Reading through the forumposts if found some howto's about how to handle this.
Some of them want to chmod the usbbus it's connected to, this only works if you never change usbslot. Then adding a line to /etc/udev/rules.d/45-libsane.rules is a more permanent solution and is also working when replugging the device. Now the problem is there is no such file in udev/rules and as there are almost no files there i suspect a change of system has been rolled out in karmic. Am i correct and if yes what system is adopted now?

Thanks

---

### Post by Favux on 2009-09-14
Hi popeye,

Check to see if in Karmic like Jaunty the udev rules are now located in "/lib/udev/rules.d/" instead of "/etc/udev/rules.d/". But I think they want you to add custom rules to the old location.

---

