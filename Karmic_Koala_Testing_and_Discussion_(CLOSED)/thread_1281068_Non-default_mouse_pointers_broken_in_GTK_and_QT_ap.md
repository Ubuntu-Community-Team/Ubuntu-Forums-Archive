---
title: "Non-default mouse pointers broken in GTK and QT apps under Compiz"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-10-02
after last update, all GTK and QT apps show the default mouse pointer even though another one is defined in "appearance".
XUL (moizilla), Gnome-Do and openoffice show the proper pointer (in my case, DMZ black), but once it exits their windows it returns to its default white.
This happens only under Compiz. Under metacity the custom pointers are shown as expected.

Are there any others who experience this issue?

---

### Post by zach4618 on 2009-10-12
I was experiencing the same problem but a restart corrected it. Seems to me that this is a bug though, since all other theme related customization is applied immediately. For new users experimenting with appearance preferences, I imagine this would cause some confusion.

---

### Post by Sand &amp; Mercury on 2009-10-12
> **zach4618 said:**
> I was experiencing the same problem but a restart corrected it. Seems to me that this is a bug though, since all other theme related customization is applied immediately. For new users experimenting with appearance preferences, I imagine this would cause some confusion.
Yep. This bug was introduced in Jaunty and hasn't been corrected since. A log out and log in fixes it.

---

