---
title: "daily gwibber (new design) doesnt work?"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by puccaso on 2010-02-02
when i run gwibber, i get nothing
when i run gwibber-preferences i get "waiting for couchdb to start." and it loops continuously..

so when i run gwibber -d (debug), i get this..
```

mahir@puccaso-lp-nix:~$ gwibber -d
DEBUG:root:Launched from /usr/bin
ERROR:dbus.proxies:Introspect error on :1.82:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
DEBUG:dbus.proxies:Executing introspect queue due to error
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 47, in <module>
    cdb.getPort()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
mahir@puccaso-lp-nix:~$ 

```

any ideas?

---

### Post by Schendje on 2010-02-02
I had that too, this afternoon. But now, a few hours later, it boots and I get the new design. It works and everything. :)

---

### Post by Framli on 2010-02-03
The same thing is happening here.
Nevertheless, it works when I launch "gwibber-service &" in a terminal before starting gwibber.

---

