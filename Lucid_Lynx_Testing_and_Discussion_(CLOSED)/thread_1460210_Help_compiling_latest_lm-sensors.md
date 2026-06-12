---
title: "Help compiling latest lm-sensors"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-22
I was told the latest sensors-applet-2.2.5 had support for ATI cards so wanted to monitor temperatures using particular drivers.
I got stuck compiling it at the ./configure stage. It asks for glib-2.0 which is installed - any ideas?
There are 2 tarballs to download:
sensors-applet_2.2.5.orig.tar.gz
sensors-applet_2.2.5-4.debian.tar.gz

I'm using the .orig. as I'm more familiar using that type but if the anyone has got the .debian. to work don't mind going with that if you can explain how.

Fully updated Lucid

---

### Post by dino99 on 2010-04-22
i'm not used with compiling but have you tried to give the full path to find that lib ( locate yourlib)

an other idea: maybe someone else i've done the job yet (search ppa or google lm-sensors+deb or rpm (can be installed with alien)

---

### Post by BrokeMahPC on 2010-04-25
Success -  I didn't have one of the .dev files installed. Compiled and working now.
Shows GPU temp through Aticonfig.
sensors-applet-2.2.5

---

