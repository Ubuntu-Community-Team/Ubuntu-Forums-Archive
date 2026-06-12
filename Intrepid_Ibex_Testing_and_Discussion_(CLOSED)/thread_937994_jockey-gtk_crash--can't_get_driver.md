---
title: "jockey-gtk crash--can't get driver"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by slugicide on 2008-10-04
When I go to System > Hardware Drivers, it askes me if I want to activate the ATI driver.  I say Activate and then it begins to download but then something called jockey-gtk crashes.  So, my question is what should I do?  Wait for a fix to come along, or find some other way to install the driver?

---

### Post by _oOMOo_ on 2008-10-04
Does Synaptic Package Manager fail to start also? If so, try running ```
sudo jockey-gtk
``` from a terminal.

---

### Post by slugicide on 2008-10-04
Synaptic starts just fine.  When I sudo jockey-gtk it crashes same as before.

```
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 344, in on_button_toggle_clicked
    'toggle', False):
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 571, in set_handler_enable
    handler_id, enable)
  File "/usr/lib/python2.5/site-packages/jockey/backend.py", line 103, in polkit_auth_wrapper
    return fn(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/jockey/backend.py", line 87, in dbus_sync_call_signal_wrapper
    raise _h_exception_exc
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 696, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.5/site-packages/jockey/backend.py", line 326, in set_enabled
    return self._f_result
AttributeError: 'Backend' object has no attribute '_f_result'

```

---

### Post by MJWitter on 2008-10-04
The same thing happened with my Nvidia driver.  Try waiting a few min, then close it down, restart the computer and try again.  When i did that it had already downloaded(in the first failed attempt), and continued to install with no problems.  Has happened on 2 installs..

---

### Post by taavikko on 2008-10-04
Try starting jockey with gksudo

```
gksudo jockey-gtk
```

Jockey is just way to automate the install of restricted drivers.
You can install manually with little effort.

---

### Post by slugicide on 2008-10-04
I can't close it down, actually.  I have to use "force quit."  Also, I have restarted my computer in the time I've been having the problem, with no new effect.

---

### Post by slugicide on 2008-10-04
No difference.  Same effect (crash).

---

