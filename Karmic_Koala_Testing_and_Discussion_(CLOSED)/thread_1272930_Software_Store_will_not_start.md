---
title: "Software Store will not start"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-09-22
Been having this problem since it was Add-Remove. Under a newly created profile it will launch so i think something has to be purged or reset. Terminal output:
```

:~$ software-store
Traceback (most recent call last):
  File "/usr/bin/software-store", line 74, in <module>
    app = SoftwareStoreApp(datadir, xapian_base_path)
  File "/usr/share/software-store/softwarestore/app.py", line 155, in __init__
    self.pending_view = PendingView(self.icons)
  File "/usr/share/software-store/softwarestore/view/pendingview.py", line 185, in __init__
    store = PendingStore(icons)
  File "/usr/share/software-store/softwarestore/view/pendingview.py", line 64, in __init__
    self.apt_daemon = aptdaemon.client.get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 475, in get_aptdaemon
    False),
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

```

Any help would be appreciated..

---

### Post by greyghost60 on 2009-09-22
Ubuntu 9.10 daily live 22/09/09. The software store does not show any
packages under free or installed. changed the server in software sources
and it appears to download but no packages are available. I don't appear
to have any installed packages either. They are all available under
Synaptic which uses the same software sources.
Reported under bug 434950

---

### Post by sports fan Matt on 2009-09-22
Upgraded from Jaunty and all works well here..I wonder why it isnt for you.

---

### Post by Regenweald on 2009-09-22
> **sox fan Matt said:**
> Upgraded from Jaunty and all works well here..I wonder why it isnt for you.

I'm pretty sure i need to delete a crap setting somewhere. I just don't know where 'where' may be. Like i said, it works under a fresh profile so it must be something i did.

---

### Post by mrsurb on 2009-09-22
I'm enjoying the same issue as the original poster. In addition, every time I run a sudo apt-get update or try to open the software-store I get an apport error stating that aptd has crashed. apt-get update still runs though.

---

### Post by ianc on 2009-09-23
I had the same problem as mrsurb. Fixed by installing rsyslog ([https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/428843](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/428843)).

But my problem was system-wide rather than for just one user, so I suspect this was a different issue to the OP's...

---

### Post by Regenweald on 2009-09-23
Fixed :)
```

sudo dpkg-reconfigure software-store

```

---

### Post by Ric_NYC on 2009-09-24
> **Regenweald said:**
> Fixed :)
```

sudo dpkg-reconfigure software-store

```

It didn't fix it. It's still crashing.


Any ideas how to fix it?

---

