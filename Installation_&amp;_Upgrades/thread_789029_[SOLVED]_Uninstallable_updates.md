---
title: "[SOLVED] Uninstallable updates"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by gwi on 2008-05-10
Since upgrading to Hardy, the update manager shows two packages which can not be selected to be installed. Why is this?

---

### Post by Pumalite on 2008-05-10
Maybe your upgrade didn't go too well. How is your computer doing?

---

### Post by gwi on 2008-05-10
The upgrade went without errors. I had four problems after the upgrade:
[LIST=1]
[*]VMware server didn't work: solved by patching and recompiling vmmon driver;
[*]VirtualBox didn't work: solved by recompiling vboxdrv module;
[*]Java applets in Firefox didn't work: solved by creating a symbolic link for the Java plugin;
[*]Wacom Graphire doesn't work: still unsolved.
[/LIST]

I think the four problems above are not related to the uninstallable updates (the first two are normal after a kernel change, and the third seems to be a "known problem").

---

### Post by Pumalite on 2008-05-10
Post:
uname -a

---

### Post by gwi on 2008-05-11
I just finished a fresh install, hoping to solve more problems. The uninstallable updates are gone now. (Unfortunately the Wacom problem is still there...)

---

### Post by Pumalite on 2008-05-11
This might help:
[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

---

