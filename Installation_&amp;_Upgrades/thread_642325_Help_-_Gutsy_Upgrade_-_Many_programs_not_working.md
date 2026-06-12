---
title: "Help - Gutsy Upgrade - Many programs not working"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Yuzem on 2007-12-16
I upgraded to Gutsy from Feisty and this is what happens when I run some programs.

gnome-screensaver (I can't lock my computer):
```
gnome-screensaver
process 6309: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4954.
This is normally a bug in some application using the D-Bus library.
  D-Bus not built with -rdynamic so unable to print a backtrace
Cancelado (core dumped)
```

comix:
```
comix
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.
```

restricted-manager
```
restricted-manager 
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 40, in <module>
    from RestrictedManager.RestrictedManagerGtk import RestrictedManagerGtk as RestrictedManager
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

software-properties-gtk
```
software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

avant-window-navigator
```
avant-window-navigator
avant-window-navigator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory
```

And the list goes on...
I will appreciate any help.

---

### Post by briandu on 2007-12-16
I assume you can get a session and that you are internet connected. 
So -----

open terminal and fire off 

apt-get update
THEN
apt-get upgrade

if the fist apt..........  fails then
fire off second.

BUT, if neither kicks in then you have a problems. 

BTW I would state that it would be better to conduct a fresh install rather than the upgrade as several folks have had strange problems (me included).

Have off you home directories and install and restore the home directories - obviously the home directories should be in a seperate partition (it really helps with this kind of actions)

PS: at boot up go to safe terminal session NOT Gnome or KDE

---

### Post by Yuzem on 2007-12-16
First of all, thank for your answer. :)

The commands work perfectly but there is nothing to update.

My home folder is in the same partition because the other is ntfs and the home folder can't be on a ntfs partition.

I just found that mirage isn't working neither:
```
mirage
Traceback (most recent call last):
  File "/usr/bin/mirage", line 26, in <module>
    import mirage
  File "/usr/lib/python2.5/site-packages/mirage.py", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```
But yes a can login and I have internet connection, firefox works :guitar:

Any other clue? :confused:

---

