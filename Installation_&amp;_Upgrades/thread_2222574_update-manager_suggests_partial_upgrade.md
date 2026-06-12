---
title: "update-manager suggests partial upgrade"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by a.m.wink on 2014-05-07
I used update-manager to perform at least the last two upgrades: from 11->12 and 12->13.
Now that the new Trusty release is out I expected it to work as it has before.

However, after some warnings
```
(update-manager:14811): dconf-WARNING **: failed to commit changes to dconf: The connection is closed
(update-manager:14811): libunity-CRITICAL **: unity-launcher.vala:154: Unable to connect to session bus: The connection is closed
warning: could not initiate dbus
(update-manager:14811): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
(update-manager:14811): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
(update-manager:14811): GLib-GIO-CRITICAL **: g_dbus_connection_get_unique_name: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

```
the update manager window changes to a message window saying:
> Not all updates can be installed.
Run a partial upgrade, to install as many updates as possible
This can be caused by:
* A previous upgrade which did not complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

When I follow the advice and click on 'partial upgrade' it says that there are no updates.

If I go through the same screen and press 'continue' (instead of 'pratial upgrade') I get a message
> Software index is broken.
It is impossible to install or remove any software right now. Pleas use the package manager 'Synaptic' or run 'sudo apt-get install -f' in a terminal to fix this issue first.

When I do that, neither synaptic nor apt-get report any problems.

One previous thread lists a similar problem, only that has not been solved:
[http://ubuntuforums.org/showthread.php?t=2159807](http://ubuntuforums.org/showthread.php?t=2159807)

Based on this thread, which identified python3.3-minimal as the culprit, I did try purging python3-* (pretty massive deletion) and re-installing only the packages that I needed.
Re-installing update-manager also re-installed some python3 packages.

Unfortunately, this has not solved the broken software index.

Does anyone know whether python3 really is the source of the problem?
Or is it possible to re-build the package index independently?

Happy to provide error messages and logs if that helps!

---

### Post by bapoumba on 2014-05-07
Would you please first post the output to :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
uname -a
sudo apt-get update
sudo apt-get upgrade
```

Please wrap [code] tags around each individual output (# symbol in the editor).

---

### Post by grahammechanical on 2014-05-07
Did you notice this

> [COLOR=#000000]*Unofficial software packages not provided by Ubuntu*[/COLOR]

When we upgrade the software sources or repositories are changed from those for the old version to those of the new version. It could be that you have Personal Package Archives (PPAs) as software sources which do not have an archive for 14.04.

I use the development branch all the time. I am used to seeing that Partial Upgrade message because the development branch does not have all the usual repositories enabled. I simply click Continue and I let the update/upgrade proceed.

Regards.

---

