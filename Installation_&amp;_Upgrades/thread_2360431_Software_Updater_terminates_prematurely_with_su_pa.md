---
title: "Software Updater terminates prematurely with su packages selected.  What gives?"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2017-05-04
On several occasions I have been forced to call sudo synaptic from GNOME&#8482; Terminal for routine Kernel package upgrades, as Software Updater *doesn't* wait for authentication on either Kernel 4.8.0-*n*-generic (Package: **linux-image-generic-hwe**) or 4.10.0-*n*-generic (Package: **linux-image-generic-hwe-edge**) - it terminates before it can call /sbin/sudo.  Additionally, several applications fail to call sudo when selected.  What configuration files could trigger this misbehavior?

**Update:**  Launching update-manager from GNOME Terminal resulted in the following:
```
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity

```

**Update 2:**  Suspect a locks problem, as /bin/debconf was unable to access a specific file for update-manager:
```
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

```

---

