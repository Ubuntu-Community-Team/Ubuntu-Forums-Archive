---
title: "Problem with make command"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by ancient on 2006-12-10
Why doent the make command work from the terminal? it says command not found.

---

### Post by yuanfangcan on 2006-12-10
seems it also happened to me. you may need to install make utility yourself. In synaptic package manager search "make", you will find it.

---

### Post by aysiu on 2006-12-10
```
sudo aptitude update
sudo aptitude install build-essential
``` The *make* command will now be available.

---

