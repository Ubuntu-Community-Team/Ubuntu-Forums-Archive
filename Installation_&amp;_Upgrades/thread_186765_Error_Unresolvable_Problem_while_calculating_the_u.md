---
title: "Error: Unresolvable Problem while calculating the upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by WoodyMahan on 2006-06-02
[B]Got the screen titled "Upgrading to Ubuntu 6.06 LTS"
Got through Preparing the upgrade AND Modifying the software channels
Error occured during Downloading and installing the upgrade
Error box text: "A unresolvable problem occurred while calculating the upgrade. Please report this as a bug."[/B]

I reported this as Bug [#47558]("https://launchpad.net/distros/ubuntu/+bug/47558")

Anyone else having this issue?


Breezy 5.10 Gnome
Here is the Terminal Text:
woody@WoodUB:~$ gksu "update-manager -d"
Sorry.
woody@WoodUB:~$ gksudo "update-manager -d"
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)

(synaptic:21928): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:21928): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:21928): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
extracting '/tmp/tmpVbF31P/dapper.tar.gz'
authenticate '/tmp/tmpVbF31P/dapper.tar.gz' against '/tmp/tmpVbF31P/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
woody@WoodUB:~$

---

### Post by ubuntu_demon on 2006-06-02
You might have to dist-upgrade by hand. Look here :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

