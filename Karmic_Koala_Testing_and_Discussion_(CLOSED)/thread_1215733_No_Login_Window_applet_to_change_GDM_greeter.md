---
title: "No Login Window applet to change GDM greeter"
date: 2009-07-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-17
Er, I don't seem to have any way to change the GDM greeter. The Login Window under System>Preferences is missing. No sign of it at all. Am I missing something?

---

### Post by BwackNinja on 2009-07-17
Yes and no - [http://ubuntuforums.org/showthread.php?t=1202843](http://ubuntuforums.org/showthread.php?t=1202843) has everything about it

---

### Post by wayne_cat on 2009-07-17
> **phenest said:**
> Er, I don't seem to have any way to change the GDM greeter. The Login Window under System>Preferences is missing. No sign of it at all. Am I missing something?

"Login Window Preferences" is not available at the moment

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)

Maybe it will come back ... but it will take some time:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig)

gdm 2.26 does not support gdmgreeter themes ... but you can change the look
a little bit:


[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

edit: to late :biggrin:

---

### Post by pelle.k on 2009-07-17
Someone should make a simple GUI to change those gconf values. Preferably with drag'n'drop. Shouldn't take many lines in pygtk/wxpython.
I'm not running karmic ATM, so i'm excused ;)

---

### Post by wayne_cat on 2009-07-17
> **pelle.k said:**
> Someone should make a simple GUI to change those gconf values. Preferably with drag'n'drop. Shouldn't take many lines in pygtk/wxpython.
I'm not running karmic ATM, so i'm excused ;)

Give them a little bit time:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig)

---

