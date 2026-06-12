---
title: "Help me in Quickly"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Praveen30 on 2011-06-17
i did install quickly earlier and it was running smoothly...then because of some reasons i had to purge quickly from my system...now i have installed it once again but when i am trying to run it, i am greeted with lots of errors in terminal, please help...

```


praveen@ubuntu:~$ quickly create ubuntu-application foobar
Creating project directory foobar
Creating bzr repository and committing
Launching your newly created project!le 0/1
Traceback (most recent call last):
  File "./foobar", line 33, in <module>
    foobar.main()
  File "/home/praveen/foobar/foobar/__init__.py", line 40, in main
    preferences.db_connect()
  File "/home/praveen/foobar/foobar_lib/preferences.py", line 50, in db_connect
    self._database = CouchDatabase(self._db_name, create=True)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 101, in __init__
    oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 75, in __init__
    oauth_tokens=oauth_tokens, ctx=ctx, views_factory=views_factory)
  File "/usr/lib/pymodules/python2.7/desktopcouch/records/database.py", line 123, in __init__
    self._reconnect()
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 81, in _reconnect
    port = find_port(ctx=self.ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/__init__.py", line 48, in find_port
    return platform_find_port(pid, ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 100, in platform_find_port
    proxy = bus.get_object('org.desktopcouch.CouchDB', '/')
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```


after running quickly run----

```

praveen@ubuntu:~$ cd foobar
praveen@ubuntu:~/foobar$ quickly run
Traceback (most recent call last):
  File "bin/foobar", line 33, in <module>
    foobar.main()
  File "/home/praveen/foobar/foobar/__init__.py", line 40, in main
    preferences.db_connect()
  File "/home/praveen/foobar/foobar_lib/preferences.py", line 50, in db_connect
    self._database = CouchDatabase(self._db_name, create=True)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 101, in __init__
    oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 75, in __init__
    oauth_tokens=oauth_tokens, ctx=ctx, views_factory=views_factory)
  File "/usr/lib/pymodules/python2.7/desktopcouch/records/database.py", line 123, in __init__
    self._reconnect()
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/server.py", line 81, in _reconnect
    port = find_port(ctx=self.ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/__init__.py", line 48, in find_port
    return platform_find_port(pid, ctx)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 100, in platform_find_port
    proxy = bus.get_object('org.desktopcouch.CouchDB', '/')
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.7/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.7/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.7/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by hackys on 2011-09-28
Same here. Running 11.04 64-bit.

I also found same issue on AskUbuntu, but with no answer. Also i got no reply on IRC, so i hope someone will look here. :)

[http://askubuntu.com/questions/61692/dbus-exception-when-using-quickly](http://askubuntu.com/questions/61692/dbus-exception-when-using-quickly)

---

