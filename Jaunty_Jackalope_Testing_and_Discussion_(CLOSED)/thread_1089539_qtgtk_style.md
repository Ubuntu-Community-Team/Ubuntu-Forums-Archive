---
title: "qtgtk style"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Voynix on 2009-03-07
I have been using the qtgtk style to make my kde applications look like real gtk native applications in ubuntu. While I am only using a very selected number of kde4 apps in jaunty, most of them retain their "out-of-place"  ** oxygenated** look and feel.  When can we have kde applications built using the right libraries to allow for a more consistent look and feel? Those who prefer gtk can still play with the qt4 config file.

---

### Post by jfernyhough on 2009-03-07
Have you installed and run qt4-qtconfig? It allows you to change the qt4 theme (qt3-qtconfig will do the same thing for qt3).

For jaunty at least, picking "Desktop settings" in qt4-qtconfig seems to mean Oxygen, btw.

---

### Post by BwackNinja on 2009-03-07
For all the apps that qt4-qtconfig doesn't work for, you can use systemsettings.

---

### Post by Voynix on 2009-03-07
Unfortunately only speedcrunch seems to take the gtk laf. Kile, for example, still has the kde4 style. I am not a kde4 hater, to be honest, but as we do have the possibility to harmonise the styles, I wonder why some kde4 applications can adopt qtgtk styles while others don't. QT4 dependencies?

---

### Post by cb951303 on 2009-03-07
> **Voynix said:**
> Unfortunately only speedcrunch seems to take the gtk laf. Kile, for example, still has the kde4 style. I am not a kde4 hater, to be honest, but as we do have the possibility to harmonise the styles, I wonder why some kde4 applications can adopt qtgtk styles while others don't. QT4 dependencies?

yeah I encountered the same problem too. Only a little bit more weird. Lyx QT4 version uses GTK style but file dialog is still QT whereas all my other qt4 applications uses native GTK file dialog :confused:

---

### Post by Voynix on 2009-03-07
systemsettings only go as far as changing the icons... the widgets and colours are still kde4ish...

---

