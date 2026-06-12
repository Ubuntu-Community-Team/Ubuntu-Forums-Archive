---
title: "feisty and gnome-app-install"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by StuietE on 2007-01-27
I have just upgraded my ubuntu desktop from edgy to feisty. I tried to  open gnome-app-install and it refused to open instead i get the following message through the terminal.

stuart@MarioLuigiLinkDK:~$ gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 213, in <module>
    sys.argv, as, transient_for)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 117, in __init__
    self.setupDbus()
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 306, in setupDbus
    proxy_obj = bus.get_object('org.freedesktop.AppInstall', '/org/freedesktop/AppInstallObject')
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 412, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 232, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 171, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.AppInstall was not provided by any .service files

Could someone please help me

thanks

---

