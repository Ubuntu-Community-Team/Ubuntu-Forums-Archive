---
title: "Software Center Crashes"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by wsccgreg2 on 2014-04-15
Neither Ubuntu Software Center nor Software Updater will open. An older post help suggested opening Software Center from terminal and posting results. So here are my results if it helps (though it doesn't help me). Any help would be appreciated. Thanks.

Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 141, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 74, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by ibjsb4 on 2014-04-15
I don't know what to tell you about the software center, but until you get it fixed, just use another package manager.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

To install using terminal:

```
sudo apt-get install synaptic

```

---

### Post by mörgæs on 2014-04-16
Don't install new stuff before we know that the package system is in good shape.
Please reboot, run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` and post the results in CODE tags.

---

### Post by ibjsb4 on 2014-04-16
> **mörgæs said:**
> Don't install new stuff before we know that the package system is in good shape.
Please reboot, run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` and post the results in CODE tags.

Updates and upgrades are a good idea, but I would maintain that if package system is broke, apt-get install will fail.

If software center is broke, apt-get install will work.

---

