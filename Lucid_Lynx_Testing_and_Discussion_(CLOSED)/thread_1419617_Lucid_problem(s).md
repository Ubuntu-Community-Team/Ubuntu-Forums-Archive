---
title: "Lucid problem(s)"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nvsbl on 2010-03-02
I upgraded to Lucid alpha 3 yesterday, and since then have been having a series of problems. Simultaneously, Gwibber and Lernid stopped working. This is quite timely, as this week is Opportunistic Developer Week, and I was looking forward to learning to work with gwibber.

I get this when I try Gwibber:
:> gwibber
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 34, in <module>
    obj = dbus.SessionBus().get_object("org.desktopcouch.CouchDB", "/")
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

This is what happens when I try to run Lernid
:> lernid 
Traceback (most recent call last):
  File "/usr/bin/lernid", line 56, in <module>
    from lernid.CouchDBPreferences import Preferences
  File "/usr/lib/python2.6/dist-packages/lernid/CouchDBPreferences.py", line 21, in <module>
    from desktopcouch.records.server import CouchDatabase
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 42, in <module>
    from desktopcouch.records.server import CouchDatabase
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 27, in <module>
    from desktopcouch.records import server_base
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 29, in <module>
    from oauth import oauth
ImportError: cannot import name oauth

Although Lernid is not expressly required to participate in UODW, I can't participate anyways because desktop-couch isn't working. Please help!

These bugs were filed [here]("https://bugs.launchpad.net/ubuntu/+source/lernid/+bug/530495") and [here]("https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/530541").

---

