---
title: "how come system-config-printer-gnome is not installed by default?"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-15
i have just tried to print from my xp computer to my linux computer then i noticed that my printer in linux is not shared when i search for printer configuration found nothing i had to manually install system-config-printer-gnome via sudo apt-get install system-config-printer-gnome command why is that?

thanks in advance.

---

### Post by pferraro on 2010-03-15
system-config-printer-gnome is a dependency of ubuntu-desktop and is therefore part of the default install.  You must have removed this package at some point.

---

### Post by aviramof on 2010-03-15
i'm sure i did no but when i check now i see that ubuntu-desktop itself is not installed which is even stranger because i sure did not removed this and i only install ubuntu a few days ago on the 12th.

---

### Post by NCLI on 2010-03-15
It probably happened if you ran a partial upgrade. If you don't know how to fix simple stuff like this, I'd advise you to go back to 9.10 for now, if you can.

---

### Post by aviramof on 2010-03-15
i never installed partial update and i never did anything thet might uninstall it i am pretty sure that it was never installed in the first place and when i install ubuntu again i will check it and report here.

---

### Post by cariboo on 2010-03-15
You can enable printer sharing on the cups web interface:

[http://localhost:631]("http://localhost:631")

Click the administration tab.

---

### Post by emarkay on 2010-03-15
Yea, that bug is still there CUPS is not enabled by default.

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/314408](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/314408)

---

