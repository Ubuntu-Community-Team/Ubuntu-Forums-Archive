---
title: "Alacarte on Jaunty Broke"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vahnx on 2009-03-27
Alacarte (Ubuntu Menu Editor) was working fine (fresh Jaunty beta install last night) until I configured my system (installed kde, xfce, wine, etc.) and now when I click Menu Editor, nothing happens. Attempted on another user, same result. Running alacarte from terminal re-produces:

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gio
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8

```

---

### Post by coffeecat on 2009-03-27
If you had been watching the Jaunty subforum, you would have seen a shower of posts about this this morning.

[See this sticky.](http://ubuntuforums.org/showthread.php?t=1107854)

Update manager is also broken, but you can use the command line or Synaptic (so long as you don't want to change repositories), because it's now been fixed with an update to the affected python packages.

Posting from a formerly-broken, now repaired Jaunty. :wink:

---

### Post by vahnx on 2009-03-27
Thanks so much. Couple of apps were broke and now fixed. Although my keyboard layout switched to Afghanistan :S but I was able to switch it back.

---

### Post by bapoumba on 2009-03-28
Moved to Jaunty.

---

