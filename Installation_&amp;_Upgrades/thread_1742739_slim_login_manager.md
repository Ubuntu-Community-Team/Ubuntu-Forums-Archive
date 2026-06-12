---
title: "slim login manager"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by kartabosh on 2011-04-29
after installing slim and selecting it as my default login manager my ubuntu won't boot anymore, does anyone know where the config file that says which login manager is default so i can revert back?

---

### Post by dino99 on 2011-04-29
its gdm on gnome system, or kdm in kde system, ...

---

### Post by kartabosh on 2011-04-29
i know that but where is the settings file so i can edit it from outside ubuntu

---

### Post by prshah on 2011-04-29
> **kartabosh said:**
> after installing slim and selecting it as my default login manager my ubuntu won't boot anymore, does anyone know where the config file that says which login manager is default so i can revert back?

You can revert back with the command ```
sudo dpkg-reconfigure gdm
``` from a terminal (Ctrl+Alt+F1) if you can't log in.

Or you can directly edit the /etc/X11/default-display-manager file: ```
Fri Apr 29 @14:26:00:~$ cat /etc/X11/default-display-manager 
/usr/sbin/gdm
```

Both solutions need a restart (of X, if not system) to take effect.

---

### Post by dimepag on 2011-04-29
nothing

---

### Post by kartabosh on 2011-04-29
i managed to get gdm back and now it works again, but why wont slim load?

---

