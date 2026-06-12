---
title: "Software Center Not Opening"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by V_Narayanan on 2015-07-16
Hi
Software Center Opens and immediately closes.
If I run in Terminal the command, I get the error message as below

Please guide me
Yours
VN

root@Lenovo-B490:/# software-center

(software-center:5228): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:16: Theming engine 'adwaita' not found
2015-07-16 23:23:19,825 - softwarecenter.ui.gtk3.app - ERROR - could not initiate dbus
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1250, in setup_dbus_or_bring_other_instance_to_front
    bus = dbus.SessionBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2015-07-16 23:23:19,976 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 140, in find_oauth_token_sync
    sso = self. _get_login_backend_and_connect()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 132, in _get_login_backend_and_connect
    _(SOFTWARE_CENTER_SSO_DESCRIPTION))
  File "/usr/share/software-center/softwarecenter/backend/login.py", line 80, in get_login_backend
    sso_class = LoginBackendDbusSSO(window_id, appname, help_text)
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 46, in __init__
    self.bus = dbus.SessionBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
root@Lenovo-B490:/#

---

### Post by v3.xx on 2015-07-16
I do not know how to fix the software center, but would suggest that you install another package manager to test.
```
sudo apt-get install synaptic
```
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

