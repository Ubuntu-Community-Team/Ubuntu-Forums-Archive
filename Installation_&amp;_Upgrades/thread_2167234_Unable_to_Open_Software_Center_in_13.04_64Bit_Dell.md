---
title: "Unable to Open Software Center in 13.04 64Bit Dell XPS 14z"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by spraveenitpro on 2013-08-12
Hi all

I am getting the following when running Software-center from terminal as clicking icon does not respond :

praveen@praveen-XPS-L412Z:~$ sudo software-center
[sudo] password for praveen: 
2013-08-13 08:36:02,868 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-08-13 08:36:11,403 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-08-13 08:36:11,403 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 141, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 75, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
praveen@praveen-XPS-L412Z:~$

---

### Post by ibjsb4 on 2013-08-13
Have you tried reinstalling it?

---

