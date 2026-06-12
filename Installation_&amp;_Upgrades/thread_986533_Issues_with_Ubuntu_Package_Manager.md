---
title: "Issues with Ubuntu Package Manager"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by maff130 on 2008-11-18
I recently installed Ubuntu 8.10 on my laptop, and after a few days of having it running smoothly, I booted today, to find that Add/Remove, and the update manager won't start. Launching them, the system appears to run, but after a short period of time, Ubuntu appears to give up. Usually I just use apt-get to install and update packages, however I loaded it today to have a look through the games.
Is there any reason why this won't even start, and is there any way I can fix this?

EDIT: I ran gnome-app-install in terminal, it reports an issue with ATK and GTK+
```
maff@mudtail:~$ gnome-app-install
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 490, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 30, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
maff@mudtail:~$
```

---

### Post by maff130 on 2008-11-19
Can anyone help me with this, at all?

---

