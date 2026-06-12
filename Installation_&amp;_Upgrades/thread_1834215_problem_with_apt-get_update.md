---
title: "problem with apt-get update"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by shubham1 on 2011-08-27
i am having a problem with apt-get upgrade when ever i try to upgrade any software it shows to upgrade all softwares i have to upgrade php
i tried 
sudo apt-get upgrade php
or any other it gives to upgrade all and ubuntu software cneter dont show upgrades how to enable ubuntu software cneter to show upgrades and tell upgrades.

---

### Post by kc1di on 2011-08-27
As far as I know there is no command in apt-get to upgrade a single package.  I believe upgrade will upgrade all installed packages on your system.  If you want to upgrade only the PHP package you will have to use synaptic or other package manager.

Hope this helps.

---

### Post by shubham1 on 2011-08-27
my ubuntu software cneter is not working.???

---

### Post by dino99 on 2011-08-27
sudo apt-get install synaptic
sudo synaptic

---

### Post by saltmarshlamb on 2011-08-27
To update a single package reinstall it

```
sudo apt-get install --reinstall *package*
```

---

### Post by shubham1 on 2011-08-28
> **saltmarshlamb said:**
> To update a single package reinstall it

```
sudo apt-get install --reinstall *package*
```
yes this is the soludtion thanks.

---

### Post by shubham1 on 2011-08-28
> **dino99 said:**
> sudo apt-get install synaptic
sudo synaptic
i already have synapatic installed on my system.i think it come preinstalled.

---

