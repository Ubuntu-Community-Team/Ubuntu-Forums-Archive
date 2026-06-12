---
title: "Updates?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by jmedina on 2007-12-04
I just installed Kubuntu 7.10 and I installed the updates. But, during the installation it gave me an error. Now, it is saying there are no updates available, How can I check and install the remaining updates?

---

### Post by ruibernardo on 2007-12-04
Hi jmedina,

to finish interrupted package installations, open a terminal and type:
```
sudo apt-get install -f
```This should end the upgrade process.

---

### Post by jmedina on 2007-12-04
Thanks. It's working!

---

