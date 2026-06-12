---
title: "Installer Crash on Acer AOD250"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by RevDurgin on 2011-02-20
Two attempts at installing, first with Ubuntu 10.10, now with Kubuntu 10.10.
Both gave same results and error:

```
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 949, in on_next_clicked
    self.dbfilter.ok_handler()
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 343, in ok_handler
    i.shutdown()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.47 was not provided by any .service files

```

On top of that, at boot it gives error messages about missing firmware "b43-open/ucode15.fw".

So needless to say, I need some community support.

---

### Post by mörgæs on 2011-02-21
Does a live boot run well with 10.10?
Have you tried 10.04.2?

---

