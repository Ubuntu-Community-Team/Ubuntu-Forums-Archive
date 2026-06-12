---
title: "Connecting to ubuntu one"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-15
In karmic I'm having major problems with ubuntu one. It seems that when you open it the first time a window in firefox comes allowing you to connect your computer to ubuntu one. However if you close this window, it will never come again and ubuntu one will be rendered forever unusable (tested on 3 computers). 

Anyone know how to force open the window to connect to ubuntu one.

This is output from terminal.
```
sashin@Laptop:~$ ubuntuone-client-applet
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/status: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
ERROR:dbus.proxies:Introspect error on com.ubuntuone.SyncDaemon:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

---

