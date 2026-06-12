---
title: "gnome-terminal in 9.04 doesn't work with Xming"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lpknnkh on 2009-02-09
When I try to connect to my Ubuntu 9.04 via XLuancher in Xming, the error says "Failed to contact the GConf daemon; exiting."

Is there any solution?

---

### Post by knedlyk on 2009-03-15
I guess I found temporary solution. You have to start gconf daemon before you start some gnome application which uses gconf. To do it, just run in terminal:
```
/usr/lib/libgconf2-4/gconfd-2 &
```
It will start gconf daemon and then you can start XLuancher or gnome-terminal from simple X session (as it was my case).

Hope it will help.

---

### Post by lpknnkh on 2009-03-15
> **knedlyk said:**
> I guess I found temporary solution. You have to start gconf daemon before you start some gnome application which uses gconf. To do it, just run in terminal:
```
/usr/lib/libgconf2-4/gconfd-2 &
```
It will start gconf daemon and then you can start XLuancher or gnome-terminal from simple X session (as it was my case).

Hope it will help.

It's still the same error:
Failed to contact the Gconf daemon; exiting.
[1]+ Exit 1           /usr/lib/libgconf2-4/gconfd-2

---

### Post by knedlyk on 2009-03-16
Can you try run *dbus-launch* or *dbus-daemon --system* firstly and then */usr/lib/libgconf2-4/gconfd-2* ?

---

### Post by lpknnkh on 2009-03-18
> **knedlyk said:**
> Can you try run *dbus-launch* or *dbus-daemon --system* firstly and then */usr/lib/libgconf2-4/gconfd-2* ?

tried again, still the same error

---

