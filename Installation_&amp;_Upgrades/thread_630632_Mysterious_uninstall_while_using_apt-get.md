---
title: "Mysterious uninstall while using apt-get"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by vikram on 2007-12-03
When I tried to install something using 
```
sudo apt-get *package *
```It automatically selected a couple of apps I havent used in a while for uninstall. I did get them installed without any issues not sure what would cause this ?

If this helps I recently upgraded from Fiesty to Gusty and the uninstalled packages were ksol and quanta both of which installed with no issues right after.

any ideas of what could cause this ?

---

### Post by Pumalite on 2007-12-03
sudo apt-get install package

---

### Post by vikram on 2007-12-03
> **Pumalite said:**
> sudo apt-get install package

sorry earlier post had a typo. I did type 

```
 sudo apt-get install *package* 
```and the package installed succesfully but before installation I got a  message that X kb was going to be downloaded and Y MB were to be freed from the database as a result of package uninstalls. the issue is that I didnt select any packages for uninstall and I am trying to understand in what cases does apt-get automatically select packages for uninstall.

---

### Post by Pumalite on 2007-12-03
Apt-get, when installing, resolves dependencies, so it does as it sees convenient for the installation of the package.

---

