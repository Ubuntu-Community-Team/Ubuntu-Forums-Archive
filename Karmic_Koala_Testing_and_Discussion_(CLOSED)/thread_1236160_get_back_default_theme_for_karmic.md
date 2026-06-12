---
title: "get back default theme for karmic"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by benjamw on 2009-08-10
I installed Karmic Koala NBR and wanted to change the look and feel a little bit so I installed Gnome-Art and all the gtk2 engines, and started playing around in the display settings, but now I can't get the default theme back.  It's not even an option in the display settings.

Is there something I can do to get it back?

If it helps, the commands I ran to get  to my current state are the following:
```
sudo apt-get install gnome-art
sudo apt get install gtk2-engines-*
```

---

### Post by gjoellee on 2009-08-10
Installing the Ubuntu packages again may help you. This should install/reinstall all the default packages.
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by benjamw on 2009-08-10
yeah, after playing around inside the package manager, i noticed that the human theme was not installed.  apparently, when i installed one of the other themes (via the -engine-*), it removed the human theme for some reason.

I reinstalled the human theme and a few other things in there I knew i was missing, and it  came back.

my desktop now looks a lot better.

thanks for the info.  i'll probably have to use that command a few times.

---

