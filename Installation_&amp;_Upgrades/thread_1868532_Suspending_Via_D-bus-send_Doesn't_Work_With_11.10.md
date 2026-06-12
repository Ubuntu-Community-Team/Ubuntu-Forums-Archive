---
title: "Suspending Via D-bus-send Doesn't Work With 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2011-10-24
After upgrading to Ubuntu 11.10 suspending is not an option on the Classic UI and doesn't work with "dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend".

Any ideas how to suspend from the command line and/or UI?

---

### Post by 2F4U on 2011-10-24
Check if you have these scripts installed

**/usr/sbin/pm-suspend**
**/usr/sbin/pm-hibernate**

They can be executed out of a terminal with root privileges (sudo).

---

### Post by user2037 on 2011-10-24
> **2F4U said:**
> 
**/usr/sbin/pm-suspend**


Pm-suspend exists, but sudo'ing it does not work. There is no sign of life from Syslog.

EDIT: More info:
Nvidia "current" version driver
Kernel 3.0.0-12-generic-pae #20-Ubuntu SMP
Suspend worked in 11.04 before the upgrade

---

