---
title: "Dbus"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by kbish on 2007-04-20
I have problem....
user@epsilon:~$ gksu "update-manager -c"
warning: could not initiate dbus
WARNING: upgradable but no canidateOrigin?!?:  xserver-xorg-core
user@epsilon:~$

---

### Post by elmerfud on 2007-04-20
I had the same dbus error when running the upgrade.  It worked anyway.  I don't know about the candidate thing.  Seems like it isn't finding your prior linux install ?

---

### Post by Tine on 2007-04-20
try: gksudo "update-manager -c -d"

worked for  me

---

