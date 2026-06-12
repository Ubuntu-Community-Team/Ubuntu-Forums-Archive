---
title: "Wine"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Shdw Shinobi on 2005-06-18
I'm having problems installing wine usign the apt-get command in Konsole. Does anyone know how to install this (sorry for this being the 3rd thread... )

---

### Post by Xian on 2005-06-18
Do you mean the apt-get command is giving you error messages?

---

### Post by Shdw Shinobi on 2005-06-18
root@Jordan:~ # apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by Xian on 2005-06-18
You probably just need to add the [extra repos](http://ubuntuguide.org/#extrarepositories).

---

### Post by Shdw Shinobi on 2005-06-18
thanks, it works great (sorry for long reply, had to go out to eat)

---

