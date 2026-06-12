---
title: "command prompt after installing graphics card driver"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by bradpurvis on 2011-02-16
as the title says i installed a graphics card driver for my nvidia card. my desktop also has integrated graphics which it was using prior to the upgrade, the new card has a dvi port which i am not using now. could this be why there is no gui? i've tried startx and it said i had no screen

---

### Post by bradpurvis on 2011-02-16
bump

it would be great if this could be solved tonight

---

### Post by sikander3786 on 2011-02-17
From the command prompt, do these commands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

The commands are case-sensitive.

If you get to the desktop, remove your current drivers, reboot and then re-install the current driver from System > Administration > Additional Drivers/Hardware Drivers.

---

