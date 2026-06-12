---
title: "ImportError: No module named dbus"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-16
Here's an example.

```
eric@kingfisher:~$ gnome-shell --replace
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 16, in <module>
    import dbus
ImportError: No module named dbus

```

This happens for any program that invokes dbus.

How do I fix this?

---

### Post by Martje_001 on 2009-08-16
Have you installed *python-dbus*? :P

---

