---
title: "get a list of meta package dependencies"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by stanwebber on 2006-08-25
is there a quick way on the commandline to find out what packages will be installed by a meta package without actually installing it i.e. php4?  i checked the apt-get man page, but nothing struck me as being applicable.  thanks

---

### Post by meng on 2006-08-25
sudo apt-get -s install php4

---

### Post by stanwebber on 2006-08-25
do you have another suggestion?  this isn't giving me a full list of dependencies, only the ones that aren't installed or configured

---

### Post by meng on 2006-08-26
Ah good point.
Then check out packages.ubuntu.com, the dependencies should be mentioned.

---

