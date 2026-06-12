---
title: "After Upgrade System Drops Out of X Before Login"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by lambdafox on 2015-08-02
After upgrading to Xubuntu 15.04 from 14.10


When I boot normally, the system drops out of X before I can log in and shows this:


```
starting version 219
[   10.800052] i2c i2c-0: Unrecognized stepping 0x45. Defaulting to ADM1026.
Welcome to emergency mode! After logging in, type "journalctl -xb" to view
system logs. "systemctl reboot" to reboot, "systemctl default" or^D to
try again to boot into default  mode. root@randypc:~#
```

I found [this conversation]("http://fixunix.com/kernel/342733-panic-about-sysfs-adm1026.html") about this problem, but I do not understand it.

I have a spare hard drive that I did a fresh install of Xubuntu Core 15.04.  I do not see this problem with that; so, I am assuming this is a configuration error and/or a problem with an installed package.  My best guess is lm-sensors, conky and their dependencies.

Please help.

---

