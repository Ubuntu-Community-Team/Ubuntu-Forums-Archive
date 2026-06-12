---
title: "nvidia card not recognized"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mevets on 2009-04-09
I recently reinstalled ubuntu jaunty it does not seem to know how to install the driver for my nvidia GeForce 7300 SE card. Before, it would prompt me to install the different versions of a driver to enable 3D support. Now, it doesnt seem to, so how do I do this manually?

PS

I just realized jockey-gtk keeps crashing and I can not run it. Its output is this:
```

  File "/usr/bin/jockey-gtk", line 25, in <module>
    import jockey.ui
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 31, in <module>
    from backend import UnknownHandlerException, PermissionDeniedByPolicy, BackendCrashError, polkit_auth_wrapper, dbus_sync_call_signal_wrapper, Backend, DBUS_BUS_NAME
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 32, in <module>
    import detection, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 32, in <module>
    import handlers, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/xorg_driver.py", line 21, in <module>
    import XKit.xutils
ImportError: No module named XKit.xutils


```

---

### Post by ibuclaw on 2009-04-09
Yes, you can install NVIDIA drivers manually. They are available from the NVIDIA website to download.

Once downloaded, logout and switch to a terminal, and login to the console
then run:
```
sudo /etc/init.d/gdm stop
```
then execute the NVIDIA-Driver-pgk.run file and follow the instructions to install it, then reboot.

If all goes well, great.

If not, run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then start X again, then look into your logs for a possible reason to the cause.

Regards
Iain

---

### Post by mevets on 2009-04-09
thanks this ended up working for me

---

### Post by ibuclaw on 2009-04-09
So NVIDIA drivers are working?

Excellent!

Since Jaunty is an active project, you'll likely see a few kernel upgrades, which may break the driver.

To automatically re-compile the NVIDIA driver after each kernel upgrade, consult this thread here: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Regards
Iain

---

