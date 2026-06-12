---
title: "Ugrading to dbus 0.60 on Ubuntu 5.10"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by rcd on 2006-03-12
Hi,
I have Ubuntu 5.10 on my laptop which has dbus version 0.36 installed by default. I need to upgrade to dbus 0.60 on this machine. How do I do this? I got the .deb files for version 0.60 of dbus, libdbus, dbus-utils etc from the dapper repositories, however I can't do the upgrade since the older version of dbus is already installed and is being used a lot by system components like the Gnome desktop.
Is there an easy way to upgrade to dbus 0.60? I currently considering the option that rather than unpgrade dbus and all its dependencies, I should just upgrade to dapper, but since dapper isin't officially released yet, don't know how stable it is.

Thx,
rc

---

### Post by o_fortuna on 2006-03-12
[QUOTE=rcd]Hi,
I have Ubuntu 5.10 on my laptop which has dbus version 0.36 installed by default. I need to upgrade to dbus 0.60 on this machine. How do I do this? I got the .deb files for version 0.60 of dbus, libdbus, dbus-utils etc from the dapper repositories, however I can't do the upgrade since the older version of dbus is already installed and is being used a lot by system components like the Gnome desktop.
Is there an easy way to upgrade to dbus 0.60? I currently considering the option that rather than unpgrade dbus and all its dependencies, I should just upgrade to dapper, but since dapper isin't officially released yet, don't know how stable it is.

Thx,
rc[/QUOTE]
Have you had a problem using dpkg to install dbus? It is pretty good about restarting services; it won't break anything (worst case scenario is you have to reboot).

I currently run dapper, and it is *fairly* stable, but expect some level of breakage and/or annoyances. The longer you wait to upgrade, the better. It's also a good idea to start from a Flight CD and not upgrade until another milestone release, just to try to minimize the bugs.

---

