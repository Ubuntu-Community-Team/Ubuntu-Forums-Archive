---
title: "Where a sessions located??"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-12
When I get to the login screen I can choose "session" (gnome, kde, fvwm etc). Where are all the config files for these options located and how do I change the default session??

---

### Post by c_dog on 2005-04-12
The session desktop configuration files are in /usr/share/xsessions. If you want a session Window Manager type to be default; GDM or KDM will ask you if you want it to be default or only for that sessionthe first time you use the new session. If you select Previous at sessions it will load the load the XDM that you used last time you started the X Server. You can also manually set  the default in the kdmrc (/etc/kde3/kdm) or gdm.conf (/etc/gdm) configuration files. It's easier to just to do it  when you pick a new session type.

---

