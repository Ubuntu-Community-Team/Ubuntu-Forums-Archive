---
title: "can't change old wine version"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by tunco on 2011-04-20
Hi,

I installed wine from software center but i can't use ie. Wine version is wine1.2.3 but i get this message

> tunc@web:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

**Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtktextview.c:3570:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)ui/pygtk/python-gtk.sh: line 6:  4995 Aborted                 python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

tunc@web:~/ies4linux-2.99.0.1$

---

### Post by Frogs Hair on 2011-04-20
Search for the Wine PPA for Ubuntu , the PPA will keep Wine updated to the latest version . It appears to be available with Ubuntu Tweak.

---

### Post by tunco on 2011-04-20
Yes i did but i get this problem still

---

### Post by chaat on 2011-04-20
> **tunco said:**
> Yes i did but i get this problem still
i uninstalled wine first and then installed from the wine-dev ppa. I've had much better luck with the dev version currently running wine 1.3.18

---

