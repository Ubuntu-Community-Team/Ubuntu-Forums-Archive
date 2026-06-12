---
title: "Change Update Server ?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Vilius on 2006-06-18
Hi,
My ISP assigned me different internet speeds for my country and for abroad.
Speed for my country is 20x faster. So, I'm thinking - maybe I can change update server to my countrys mirror server and make updates faster ?
How to do that(if it is possible) ?

thanks
Vilius

---

### Post by Mirrorball on 2006-06-18
Type

```
sudo gedit /etc/apt/sources.list
```

at a terminal window and edit the file to change the servers.

---

