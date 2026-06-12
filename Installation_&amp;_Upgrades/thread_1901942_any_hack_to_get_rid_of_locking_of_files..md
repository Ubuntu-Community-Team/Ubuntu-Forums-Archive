---
title: "any hack to get rid of locking of files."
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by ron2794 on 2011-12-29
i am sick waiting for one installation to finish from the internet because it don't give a lock to other command unless its installation finishes.
and i get an error message. Can't get a lock.
Is there any way I can queue the command so that as soon as the installation of application finishes second one starts automatically.

---

### Post by oldos2er on 2011-12-29
How are you installing these packages? You can use one *apt-get install* command to install multiple packages: ```
sudo apt-get install <package1> <package2> <package3>
``` etc.

---

