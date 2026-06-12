---
title: "upgrade failed read this I have no panel in gnome"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by rogerb51 on 2008-10-08
I'm using the latest beta and during upgrade
it locked. The terminal was displaying something like bluez db update. When I rebooted first time got errors in my boot drive second time it booted it gnome came up but didn't have a panel and alot of errors (not configured after upgrade)
 Is is there a way to force the update to finish or repair the db.

---

### Post by Partyboi2 on 2008-10-08
Open a terminal (ctrl+Alt+F2) and try
```
sudo dpkg --configure -a
``````
sudo apt-get upgrade
```

---

### Post by rogerb51 on 2008-10-08
do I need to reboot 

gnome-panel won't start

---

### Post by Partyboi2 on 2008-10-08
Are you able to get to a terminal by pressing Ctrl+Alt+F2?

---

