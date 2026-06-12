---
title: "how to view the available updates"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by kinka-dzs on 2007-11-22
HI lads, 
sorry does anyone know how to view the possible updates of the packages from console after

sudo apt-get updates 

Synaptic does. I reallly don't want to go through the man pages today!! thank you.

---

### Post by bongobonga on 2007-11-22
I'm not sure if there is an official way of doing it, but by simply doing an 'sudo apt-get upgrade' you will be given a list all the upgrades that are available to be updated for your system. When it asks you for confirmation, which it always will, just so no so as not to install all the upgrades.

---

### Post by Meserias on 2008-01-08
It's this right solution ?
```
sudo apt-get dist-upgrade
```
:confused:

---

### Post by zvacet on 2008-01-08
No it is not.That means you want to upgrade to next version.Try 

```
sudo apt-get upgrade
```

---

