---
title: "Install gcc on amd64 10.04 without internet conenction"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by mathi.mika on 2011-12-03
My wired network which Intel Pro 10/100/1000 was unclaimed when i ran lshw -C network.

I tried to install drivers for intel website, when i ran make install command on the driver it is compiler not found.

I tried to install GCC with apt-get command. But there seems to be lot of dependencies. I just cant install gcc. 

I am really new to linux, Please help me install gcc or resolve network card issue.

---

### Post by zvacet on 2011-12-03
So you have working network when you can go to the intel website?if that is a case run 


```
sudo apt-get install build-essential
```

---

