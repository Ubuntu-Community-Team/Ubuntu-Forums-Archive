---
title: "Configure a new monitor"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by herot on 2007-04-18
i have installed a new monitor and i want to reconfigure the monitor settings.  how do i use the same method the installer used to "auto-detect" and configure it?

---

### Post by spd106 on 2007-04-18
This command will allow you to re-configure the X server, it will automatically generate a backup file in case you make a mistake.

```
sudo dpkg-reconfigure xserver-xorg
```

---

