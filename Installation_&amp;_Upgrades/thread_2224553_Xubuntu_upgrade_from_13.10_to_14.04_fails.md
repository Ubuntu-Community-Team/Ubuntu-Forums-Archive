---
title: "Xubuntu upgrade from 13.10 to 14.04 fails"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2014-05-16
Trying to upgrade my system by using Software Updater, it shows me that 14.04 is available but when I click "upgrade now" the GUI just closes and nothing happens. So I check what command that is by using the menu editor and it shows me it's just running [/code]/usr/bin/update-manager[/code] so I then run the command from the terminal and this is what it returns after I click on "upgrade now"
```
ERROR:root:Could not find any typelib for Dbusmenu
ERROR:root:Could not find any typelib for Unity
WARNING:root:can not import unity GI cannot import name Dbusmenu

(update-manager:2799): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:3274:48: Expected ',' in color definition
Checking for a new Ubuntu release

(do-release-upgrade:2872): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:3274:48: Expected ',' in color definition

** (do-release-upgrade:2872): WARNING **: Failed to load shared library 'libwebkitgtk-3.0.so.0' referenced by the typelib: libGL.so.1: cannot open shared object file: No such file or directory
/usr/lib/python3/dist-packages/gi/_gobject/__init__.py:58: Warning: cannot derive 'DistUpgrade+ReleaseNotesViewerWebkit+ReleaseNotesViewerWebkit' from non-derivable parent type 'void'
  _gobject.type_register(cls, namespace.get('__gtype_name__'))
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 152, in <module>
    fetcher.run()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 274, in run
    if not self.showReleaseNotes():
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py", line 71, in showReleaseNotes
    res = self._try_show_release_notes_webkit()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py", line 81, in _try_show_release_notes_webkit
    from .ReleaseNotesViewerWebkit import ReleaseNotesViewerWebkit
  File "/usr/lib/python3/dist-packages/DistUpgrade/ReleaseNotesViewerWebkit.py", line 35, in <module>
    class ReleaseNotesViewerWebkit(WebKit.WebView):
  File "/usr/lib/python3/dist-packages/gi/types.py", line 175, in __init__
    super(GObjectMeta, cls).__init__(name, bases, dict_)
  File "/usr/lib/python3/dist-packages/gi/_gobject/__init__.py", line 46, in __init__
    cls._type_register(cls.__dict__)
  File "/usr/lib/python3/dist-packages/gi/_gobject/__init__.py", line 58, in _type_register
    _gobject.type_register(cls, namespace.get('__gtype_name__'))
RuntimeError: could not create new GType: DistUpgrade+ReleaseNotesViewerWebkit+ReleaseNotesViewerWebkit (subclass of void)

```
This is a fresh install of 13.10, meaning it wasn't an upgraded system. I've been running 13.10 for a couple of months on this hardware and wanted to finally make the jump to 14.04. Any suggestions as to how to fix this?

---

### Post by dannyboy79 on 2014-05-17
apparently i just had to launch the update-manager command with gksudo. go figure, why would update-manager be within the menu pulldown without having gksudo in the command? so just to be clear the way that I got the upgrade to work was by entering the following command in a terminal
```
gksudo update-manager
```

---

