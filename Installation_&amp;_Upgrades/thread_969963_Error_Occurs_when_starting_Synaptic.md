---
title: "Error Occurs when starting Synaptic"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by beanpole136 on 2008-11-03
I recently installed Ubuntu 8.10 via Wubi; the installation was flawless and I installed extras such as compizconfig, emerald, and the restricted ubuntu extras. For some reason, I am now unable to start Synaptic. I get the following error:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

---

### Post by tuxxy on 2008-11-03
Open a terminal and enter this command

```
sudo dpkg --configure -a
```

---

### Post by beanpole136 on 2008-11-03
Ok sorry for the trouble. I fixed the problem by running 
```
sudo dpkg --configure -a
```
and then updating the apt
(```
sudo apt-get update
```)

Thanks anyway!

EDIT: Thanks tuxxy, I was writing this post before I saw yours. Either way, your advice would have worked!

---

