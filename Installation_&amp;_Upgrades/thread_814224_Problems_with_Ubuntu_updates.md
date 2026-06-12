---
title: "Problems with Ubuntu updates"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by K.Morgan on 2008-05-31
Ubuntu 8.04 is telling me that i have updates ready to install but when i got to install them i get this message:

'Not all updates can be installed

Run a partial upgrade, to install as many updates as possible'.


I then click the button that says partial upgrade where i then get a message saying:


'Could not resolve the upgrade

A unresolvable problem occurred while calculating the upgrade'.


This happens everytime I've tried to update all day

Does anybody know what is going on here and how i resolve it.

Kristian

---

### Post by bapoumba on 2008-05-31
Please post your sources.list:
```
cat /etc/apt/sources.list
```
and the errors to:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by K.Morgan on 2008-05-31
All is sorted now.  Running the updates from within terminal seemed to sort the problem out.

thanks

---

### Post by bapoumba on 2008-05-31
You're welcome :)

---

