---
title: "Latest update kernel 19- problems relating to permissions?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by ptipton on 2008-06-19
Have just installed the latest updates which include the 2.6.24.19 kernel and  have a bunch of different problems which seem to relate to changes permissions:
1. Ktorrent wont run from the menu ( am running in gnome btw) but if start from terminal using sudo will run  but gives errors "/var/tmp/kdecache-administrator is owned by uid 1000 instead of uid0
2.Mythtv backend cant connect to the database
3.When I try to shutdown using the menu , the menus disappear from the screen and then system freezes and have to do a hard reboot

Seems like these problems relate to ownerships and groups but when I try and view a group using the Users and groups menu everything is greyed out and cant actually change anything.

Any help much appreciated

---

### Post by buntunub on 2008-06-20
> **ptipton said:**
> Have just installed the latest updates which include the 2.6.24.19 kernel and  have a bunch of different problems which seem to relate to changes permissions:
1. Ktorrent wont run from the menu ( am running in gnome btw) but if start from terminal using sudo will run  but gives errors "/var/tmp/kdecache-administrator is owned by uid 1000 instead of uid0
2.Mythtv backend cant connect to the database
3.When I try to shutdown using the menu , the menus disappear from the screen and then system freezes and have to do a hard reboot

Seems like these problems relate to ownerships and groups but when I try and view a group using the Users and groups menu everything is greyed out and cant actually change anything.

Any help much appreciated

As far as the mythbackend, try running -

```
sudo dpkg-reconfigure mythtv-database
```

When thats done, restart the backend -

```
sudo /etc/init.d/mythbackend restart
```

For the GNOME related stuff, it looks like dbus is having issues possibly. Try restarting that via

```
sudo /etc/init.d/dbus restart
```

see if that fixes things.

---

