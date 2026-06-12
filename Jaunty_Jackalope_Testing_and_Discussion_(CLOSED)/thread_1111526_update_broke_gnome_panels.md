---
title: "update broke gnome panels"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Riffer on 2009-03-30
Did an update from Ibex to Jaunty and now I can't access my panels.  I can see them but when I click on them nothing happens.  I can't get into menus or anything.  Tried reinstalling Ubuntu Desktop didn't help.  Thoughts?

---

### Post by drs305 on 2009-03-30
If you want to try to reset the panel to defaults run the command below. You will lose any customizations (but you can save them via another gconf command: *gconftool-2 --dump /apps/panel >~/Desktop/panel*):
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel 
```

You could also try purging and reinstalling gnome-panel and gnome-panel data, although they are part of the ubuntu-desktop.

---

### Post by Riffer on 2009-03-30
thanks that seemed to fix it.

---

