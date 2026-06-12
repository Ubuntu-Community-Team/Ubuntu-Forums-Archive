---
title: "libsdl1.2debian kept back... Gnome start error"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by globetrotters1 on 2006-07-22
After upgrading from Breezy to Dapper, one of the packages have been kept back: libsdl1.2debian

I tried to install it without success. ](*,) 

When I start now the system, Gnome reports the following after a long waiting time:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

GNOME will still try to restart the Settings Daemon next time you log in."

I'm not very familiar with Ubuntu Linux and don't know how to solve this problem. I would appreciate any help!

Martin
globetrotters1

---

### Post by mlind on 2006-07-22
Did the upgrade process display any errors?

What happens if you execute following commands on terminal
```

sudo aptitude update
sudo aptitude dist-upgrade

```

Could you also post your /etc/apt/sources.list

---

