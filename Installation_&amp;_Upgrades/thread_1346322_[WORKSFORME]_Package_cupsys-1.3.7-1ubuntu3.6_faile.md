---
title: "[WORKSFORME] Package cupsys-1.3.7-1ubuntu3.6 failed to install/upgrade"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2009-12-04
As many of you may be aware, several Users have had problems with installation of certain Packages when SELinUX is enforcing.  I had the same issue attempting to get the Common UnIX Printing System reloaded on my Everex; specifically, from Synaptic, the APT_Get backend hit a consistent crash point resulting in the following output:
```
Setting up cupsys (1.3.7-1ubuntu3.6) ...
/usr/share/themes/ubuntulooks-aquagreen-alt/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
 * Starting Common Unix Printing System: cupsd
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 127
```This didn't occur in single-user mode, and I could install the balance of the related packages from normal operation.

Any help in what to watch out for in the event of a similar reaction with other Debian packages would be appreciated.

---

