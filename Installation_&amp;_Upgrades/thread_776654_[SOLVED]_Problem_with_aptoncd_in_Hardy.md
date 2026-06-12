---
title: "[SOLVED] Problem with aptoncd in Hardy"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by fourscore on 2008-04-30
The restore option in aptoncd does not work in Hardy.  When we click on the Load button  nothing happens.
Is there any fix for this bug.

---

### Post by Pumalite on 2008-04-30
AptOnCD is to restore programs to the same OS.(after a reinstall or in a different computer)

---

### Post by fourscore on 2008-04-30
> **Pumalite said:**
> AptOnCD is to restore programs to the same OS.(after a reinstall or in a different computer)
How enlightening!  I know that.
I am trying to load the  downloaded programs onto another pc. I am unable  to load the iso file created by aptoncd as the  Load button does not respond. This seems to be a bug in Hardy.
Tried running under root from terminal. The error msg recd when clicking on Load button is given below.

[HTML]user@desktop:~$ sudo aptoncd
[sudo] password for user: 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/APTonCD/restore/restoreWindow.py", line 209, in on_btnLoadFrom
    drives = bus.get_devices()
  File "/usr/lib/python2.5/site-packages/APTonCD/core/dbus_helper.py", line 38, in get_devices
    if vol.GetPropertyBoolean("volume.is_disc") and vol.GetPropertyBoolean("volume.disc.has_data"):
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "(unset)" member "GetPropertyBoolean" error name "(unset)" destination ":1.5")[/HTML]

How do I fix this problem.

---

### Post by Pumalite on 2008-05-01
Burn a new ApOnCD and make a new copy. Looks like a bad burn or a bad copy.

---

### Post by fourscore on 2008-05-01
> **Pumalite said:**
> Burn a new ApOnCD and make a new copy. Looks like a bad burn or a bad copy.

You are missing the issue.  In the Gutsy version When we click on Load button a box opens asking for which iso file to be loaded.  

In the Hardy version  this does not happen.  I keep clicking on the  Load button and there is no response.   The error log msg is posted in my earlier  post.

The problem is either in the new aptoncd version for Hardy or something in Hardy that conflicts.
Pls help.

---

### Post by fourscore on 2008-05-03
This is a reported bug. See link - [https://bugs.launchpad.net/ubuntu/+source/aptoncd/+bug/199600](https://bugs.launchpad.net/ubuntu/+source/aptoncd/+bug/199600)

---

### Post by Bri0 on 2008-05-07
In the meantime do this.

[B]
- extract the ISO (right click on it and hit 'Extract Here')[/B]

**- In terminal:**
Note: change "you:you" to your username that you login with.

sudo chown you:you /var/cache/apt/archives

Enter, then your password, Enter


This will give you permission of that folder in the filesystem ( /var/cache/apt/archives ), then copy over the packages (in the packages folder) from the extracted ISO to the archive folder (Filesystem/var/cache/apt/archives).

[B]
- Once done go into terminal and put this in, which will bring the folder back to root permission.[/B]

sudo chown root:root /var/cache/apt/archives

Enter

---

### Post by rogerdean on 2008-05-31
i've found a stopgap solution by removing aptoncd using synaptic, and then installing the version downloaded from the aptoncd site - [http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb](http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb)

---

### Post by rogerdean on 2008-05-31
and now there's a fix for aptoncd coming. in the meantime you can install the unreleased fix from 

[http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb](http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb)

---

### Post by Ansenyi on 2008-06-06
Nice, I hope this would be added to the Ubuntu repositories aswell.

---

### Post by norwoods on 2008-06-23
the aptoncd in the Ubuntu repositories is not in sync with its dependencies.

---

### Post by fourscore on 2008-06-24
> **norwoods said:**
> the aptoncd in the Ubuntu repositories is not in sync with its dependencies.

The official fix has been finally released. This now also includes the dependencies viz. python-central updated version.
Closing this as solved.

---

