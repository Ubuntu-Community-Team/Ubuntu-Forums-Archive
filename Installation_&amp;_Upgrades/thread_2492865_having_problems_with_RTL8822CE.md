---
title: "having problems with RTL8822CE"
date: 2023-11-25
forum: Installation &amp; Upgrades
---

### Post by damianmg9 on 2023-11-25
I tried installing some drivers I found on github but it does not work for me, can someone help me with it? I am using Ubuntu 23.10

---

### Post by VMC on 2023-11-25
What is output from this command:
```
lspci -knn | grep Audio -A3
```

---

### Post by jeremy31 on 2023-11-25
Post results from terminal for ```
rfkill list; lshw -c net
```

---

