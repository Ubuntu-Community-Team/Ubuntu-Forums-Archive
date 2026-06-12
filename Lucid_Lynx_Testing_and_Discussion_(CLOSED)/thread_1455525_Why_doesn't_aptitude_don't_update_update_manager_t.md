---
title: "Why doesn't aptitude don't update update manager time of last update?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-16
i have been told here in this thread that aptitude don't update update manager time of last update and i checked it with the command i made

```
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade
``` and it seem to be true so why is that and is it a bug that need to be fix?

[http://ubuntuforums.org/showthread.php?t=1454777](http://ubuntuforums.org/showthread.php?t=1454777)

thanks in advance.

---

### Post by aviramof on 2010-04-16
does any body know?

---

### Post by philinux on 2010-04-16
> **aviramof said:**
> does any body know?

Simple. Update-manager is the GNOME **APT** update manager. Also, synaptic is a graphical package management tool based on GTK+ and APT. Synaptic and update-manager use APT and aptitude is a separate thing all together.

Aptitude is a terminal-based package manager.

---

### Post by cariboo on 2010-04-16
Update manager was held back for a while yesterday 15/04/2010, but it upgraded later on in the day.

You don't need to run the command the way you did.

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Is all you need to upgrade.

---

### Post by aviramof on 2010-04-16
thanks for the information.

---

