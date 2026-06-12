---
title: "apt-get install problem"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by linux_noob0 on 2010-02-15
after installing wubi, i tried to get some basic stuff i need, such as the vim editor and g++ compiler... apt-get doesn't work, it says: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim has no installation candidate

anyone knows how to solve that? thanks!

---

### Post by r_s on 2010-02-15
sudo apt-get update

---

### Post by linux_noob0 on 2010-02-15
right... i've let the update manager work, so i tried some multitasking :/
thanks... i didn't know you can't get stuff without updating first :)

---

### Post by r_s on 2010-02-15
It needs to get all the information from the repositries.

---

