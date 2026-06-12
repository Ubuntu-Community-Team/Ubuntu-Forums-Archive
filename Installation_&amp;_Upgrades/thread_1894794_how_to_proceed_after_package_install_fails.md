---
title: "how to proceed after package install fails"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by rajadileepkolli on 2011-12-13
when i tried to upgrade from 11.04 to 11.10 using update manager during the installation of packages power failure occurred, when i tried to loin normally it is not allowing but when i tried recovery option i can login .
When i logged in it showed 810 packages there to install. can some one help me to install those 810 packages from recovery mode.

sudo apt -get install or sudo apt -get install also not working.

---

### Post by zvacet on 2011-12-14
When you are in recovery mode you don´t need sudo.Let try with 

```
apt-get update && apt-get upgrade
```If still no luck then

```
dpkg --configure -a
apt-get -f install
```

---

