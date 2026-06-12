---
title: "after upgrade to 12.04: ImportError: cannot import name PyGIDeprecation"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by stormy3 on 2015-04-12
Was on 10.04, upgraded to 12.04, all went clean.  I thought to move to 14.04, but after typing the do-release-upgrade, decided to wait a week and use 12.04, so, typed NO to the upgrade (if to proceed), it said, rolling back system to prior state, and ever since then, cannot run many tools, they all complain as follows:

ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from gi.repository import GObject, Gio
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GObject.py", line 32, in <module>
    from gi import PyGIDeprecationWarning
ImportError: cannot import name PyGIDeprecationWarning


OR:

# ubuntuone-installer
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-installer", line 19, in <module>
    from gi.repository import Gtk, GLib
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 24, in <module>
    from gi.repository import GObject
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GObject.py", line 32, in <module>
    from gi import PyGIDeprecationWarning
ImportError: cannot import name PyGIDeprecationWarning

and many such tools:

# jockey-text -l
Traceback (most recent call last):
  File "/usr/bin/jockey-text", line 20, in <module>
    import jockey.ui
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 37, in <module>
    from backend import UnknownHandlerException, PermissionDeniedByPolicy, \
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 29, in <module>
    from gi.repository import GObject
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GObject.py", line 32, in <module>
    from gi import PyGIDeprecationWarning
ImportError: cannot import name PyGIDeprecationWarning



Tried to reinstall, reinit 10's of packages, rebooted, and not able to figure it.

Who is defining this symbol, and how can I reinstall that piece?

Already tried to reinstall python-gi python-gobject and many similar, but no luck.

also, apt-get update, check, upgrade, dist-upgrade, all come right away,clean without any errors.

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

Thanks for any tips.

Stormy.

---

### Post by stormy3 on 2015-04-14
I've given up on 12.04, and despite the state of the system, 95% of things working, but some tools fail as above, decided to do a release update to 14.04, it all went clean, more or less, and this error vanished.. Not sure yet what defines that symbol, etc. but it sort of went away with a full update to 14.04.

---

### Post by dino99 on 2015-04-14
moving from LTS to LTS is supposed to have been fully tested, but you have hit a classic error transition often met in such a case (missing some break/replace on python versions here)
that is why a fresh install is way better than a dist-upgrade. Take time to clean your system now: autoremove, gtkorphan, then run update/ apt-get install -f, and finally sudo dpkg --configure -a

---

