---
title: "Could not initialize the package information"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by nutz on 2007-06-22
I got this error after AssaultCube failed to install from .deb

How would I correct this?

---

### Post by nutz on 2007-06-22
This is what I get when I try to open synaptic...

---

### Post by nutz on 2007-06-22
nutz@nutz:~$ sudo dpkg --configure -a
Password:
nutz@nutz:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package assaultcube-data needs to be reinstalled, but I can't find an archive for it.
nutz@nutz:~$

---

### Post by nutz on 2007-06-23
This fixed it...

```
sudo dpkg --remove --force-remove-reinstreq assaultcube-data
```

---

### Post by Palmonostora on 2007-07-18
Thank U so much, I had the same message (for secondlife-install) and it´s fixed now.

---

### Post by condonm on 2007-10-14
Thanks a ton! I was getting the same error as well!

---

### Post by Ehtetur on 2007-12-05
> **nutz said:**
> ```
sudo dpkg --remove --force-remove-reinstreq assaultcube-data
```

Many thanks for the un-fubar command... That really saved me!

---

### Post by fares1 on 2008-01-27
sudo dpkg --remove --force-remove-reinstreq secondlife-install


that work with me
thant you

---

