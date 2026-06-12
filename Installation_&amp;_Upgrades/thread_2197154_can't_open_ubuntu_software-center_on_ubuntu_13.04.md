---
title: "can't open ubuntu software-center on ubuntu 13.04"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by yuan-bo-august on 2014-01-02
I can't open the ubuntu software-center today, after I run the command: sudo software-center, I got the following message:

2014-01-03 01:08:04,457 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-01-03 01:08:04,675 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2014-01-03 01:08:04,675 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
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

anyone could help me ?

---

### Post by ian-weisser on 2014-01-02
What happens when you don't use sudo?

---

### Post by yuan-bo-august on 2014-01-03
the same output...

ps: I have installed the pyqt5 a few days before

---

### Post by plucky on 2014-01-03
> **yuan-bo-august said:**
> the same output...

ps: I have installed the pyqt5 a few days before

What happens if you open a terminal and run ```
sudo apt-get update && sudo apt-get upgrade
```

Post back the output if any errors.


Good Luck

---

### Post by yuan-bo-august on 2014-01-03
thx, but there were no errors when update and upgrade, I guess it would be sth wrong with the pyqt, I run the command "make uninstall" to remove the pyqt5, but the problem still remain, I don't know how to clean the pyqt5 and restore the pyqt4. BTY, I installed the pyqt5 with the source code not from apt-get or deb package.

---

