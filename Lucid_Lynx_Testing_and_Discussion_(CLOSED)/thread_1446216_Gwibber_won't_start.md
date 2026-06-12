---
title: "Gwibber won't start"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Shadow12313 on 2010-04-03
I tried starting gwibber after updating to lucid links and nothing happened.  So I tried starting it from the terminal and it returned this:

/home/ben/.themes/Oversword Dark V4.6/gtk-2.0/panel.rc:66: Unable to locate image file in pixmap_path: "/arrows/arrow-up-panel.png"
/home/ben/.themes/Oversword Dark V4.6/gtk-2.0/panel.rc:70: Overlay image options specified without filename

** (gwibber:20974): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:20974): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:20974): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 4, in <module>
    import desktopcouch, pycurl, oauth, threading, urllib, re, json
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 292, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 232, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 91, in __init__
    {'desktopcouch': 'basic'})
gnomekeyring.IOError


Any ideas?

---

### Post by phidia on 2010-04-03
I would refer to the community docs [here]("https://wiki.ubuntu.com/Gwibber") for gwibber and reinstall it based on that guide.

---

### Post by nopayne on 2010-04-04
I had the same problem.  I got around it by starting the gnome keyring service: gnome-keyring-daemon

---

### Post by toupeiro on 2010-04-04
> **phidia said:**
> I would refer to the community docs [here]("https://wiki.ubuntu.com/Gwibber") for gwibber and reinstall it based on that guide.

This defeats the purpose of Lucid testing..  There is a bug report submitted:

[https://bugs.launchpad.net/bugs/552227](https://bugs.launchpad.net/bugs/552227)

Apparently, this doesn't appear to be an issue in the live-CD according to some testers.

---

