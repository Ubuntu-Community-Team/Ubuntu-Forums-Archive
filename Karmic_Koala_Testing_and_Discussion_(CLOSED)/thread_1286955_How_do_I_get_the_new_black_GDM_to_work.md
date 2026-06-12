---
title: "How do I get the new black GDM to work?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-10-09
For some reason I have the old grey GDM and cannot get the black one to work? I clicked on the high contrast option and that made things worse. Any help?

Thanks.

---

### Post by taavikko on 2009-10-09
> **bridgetothesun said:**
> For some reason I have the old grey GDM and cannot get the black one to work? I clicked on the high contrast option and that made things worse. Any help?

Thanks.

Change the theme
```
sudo -u gdm gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme HumanLogin
```

I would try to unset every key.
```
sudo -u gdm gconftool-2 --recursive-unset /desktop/gnome/
```

---

### Post by ikisham on 2009-10-09
Also when I first installed the beta (alternate cd image), the gdm was the old one. After an update (partial, by the way, I hadn't read the alert not to do it) came in the new one.
So in case you doesn't have it installed, hold on and wait till the update manager asks for an update, which may happen only further ahead.

---

