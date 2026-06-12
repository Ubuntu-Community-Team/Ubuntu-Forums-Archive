---
title: "python-gtk problems after 8.10 upgrade"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by ktenney on 2008-11-10
Howdy,

I recently upgraded my laptop to 8.10, when I try jockey-gtk (for example) I get the following:

ktenney@lappy:~$ jockey-gtk
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import gio
ImportError: could not import gio
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 23, in <module>
    import glib, gtk, gtk.glade, gobject, pynotify
ImportError: cannot import name Widget from gtk

I've done 
$> apt-get install xxx --reinstall
for python-gtk2 and others, still no good.

Suggestions?

Thanks,
Kent

---

### Post by sukhhari on 2008-11-11
Else try using at Ubuntu Recovery Mode and re-fix the Problematic dkpg option.

:)

---

### Post by Nicole on 2008-11-23
Did you find a solution to this? I'm having a similar problem (as, so the search suggests are other people) - if anyone's found a solution short of nuking the whole thing and starting over, please share!

Thank you!

N

---

### Post by pinio on 2010-01-10
I have similar problem. When i try run jokosher:
```

pinio@piniobook:~$ jokosher
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import gio
ImportError: could not import gio
Traceback (most recent call last):
  File "/usr/local/bin/jokosher", line 97, in <module>
    import Jokosher.JokosherApp as JokosherApp
  File "/usr/local/lib/python2.6/dist-packages/Jokosher/JokosherApp.py", line 13, in <module>
    import gtk.glade, gobject
ImportError: cannot import name Widget from gtk

```
My system is Xubuntu Lucid, upgrade to newest package.

---

