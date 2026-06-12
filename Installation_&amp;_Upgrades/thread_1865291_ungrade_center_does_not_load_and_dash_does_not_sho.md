---
title: "ungrade center does not load and dash does not show apps"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by shredready on 2011-10-19
just ungraded to unbunto 11 64 bit and now soft center does not load and dash does not show or load any apps

any help would be greatly appreciated

---

### Post by shredready on 2011-10-20
> **shredready said:**
> just ungraded to unbunto 11 64 bit and now soft center does not load and dash does not show or load any apps

any help would be greatly appreciated

I typed in software center in the terminal and got this



software-center
2011-10-20 16:51:40,475 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-20 16:52:07,825 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2011-10-20 16:52:07,825 - dbus.proxies - ERROR - Introspect error on :1.122:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2011-10-20 16:52:36,276 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-20 16:52:36,446 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css

---

### Post by shredready on 2011-10-20
> **shredready said:**
> I typed in software center in the terminal and got this



software-center
2011-10-20 16:51:40,475 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-20 16:52:07,825 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2011-10-20 16:52:07,825 - dbus.proxies - ERROR - Introspect error on :1.122:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2011-10-20 16:52:36,276 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-20 16:52:36,446 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css

I uninstalled and reinstalled and get this error

software-center
2011-10-20 22:04:29,818 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-20 22:04:32,419 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 158, in _get_new_xapiandb
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3408, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-10-20 22:04:33,301 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-20 22:04:33,687 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css

---

### Post by Matt 6:27 on 2011-10-24
So you don't feel alone... I've the same issue with a 64 bit install of Oneiric.  I haven't ID'd cause or cure yet, but hope springs eternal.

---

### Post by sirvinniei on 2011-11-29
having the same problem
only solution i can find is reinstalling ubuntu which I am not going to do
[https://answers.launchpad.net/ubuntu/+source/software-center/+question/177062](https://answers.launchpad.net/ubuntu/+source/software-center/+question/177062)

---

