---
title: "Lubuntu 10.10 to Ubuntu 11.04 hangs/libc6"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by dOlOb on 2011-05-18
I can not perform the upgrade.

Installing upgrades hangs at configuring libc6

xscreensaver and xlockmore must be restarted before upgrading

One or more running instances of xscreensaver or xscreensaver have been detected on this system.  Because of incompatible library changes, the upgrade of the GNU libc library will leave you unable to authenticate to these programs.  You should arrange for these programs to be restarted or stopped before continuing this upgrade, to avoid locking your users out of their current sessions.

I've stopped xscreensaver it is the only session running.  I will reboot and stop xscreensaver and then run the upgrade.

---

### Post by dOlOb on 2011-05-18
shuttinh down the offending process then starting the update is working so far.

---

