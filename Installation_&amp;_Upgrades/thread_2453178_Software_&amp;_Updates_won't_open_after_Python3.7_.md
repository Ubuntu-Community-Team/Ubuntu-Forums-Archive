---
title: "Software &amp; Updates won't open after Python3.7 installation"
date: 2020-11-04
forum: Installation &amp; Upgrades
---

### Post by wbadry on 2020-11-04
Hello,
I have installed Python3.7 due to requirements. Ubuntu 18.04 is already coming with Pyrhon 3.6. However, after installation, I am unable to run "software and Updates" application. I made sure that Python 3.6 is the default Python3.

When debugging the problem, I get this error when running ```
software-properties-gtk
```

```

wbadry@TTS-UBUNTU:~$ software-properties-gtk 
ERROR:dbus.proxies:Introspect error on :1.205:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 173, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.205 was not provided by any .service files

```

All help is appreciated. By the way, **livepatch** application is affected as well.

---

### Post by TheFu on 2020-11-05
The system version of python cannot be changed safely.

If you need a different version for some other need, use an environment management solution like **pyenv** just for those other programs.

Don't mess with the system tools (python, perl, ruby, etc) on any Linux system.  You will break things, as you've learned.

Put it back the way it was before.

---

