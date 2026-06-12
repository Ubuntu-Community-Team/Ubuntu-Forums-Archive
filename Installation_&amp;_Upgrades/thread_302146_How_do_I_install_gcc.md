---
title: "How do I install gcc?"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by puffidredz on 2006-11-18
I am a noob to Linux and have Ubuntu Dapper. I am attempting to install the drivers for my Nvidia Geforce 7600 card but in the installation it stops and gives me error that it cannot find cc and I need to install gcc. How do I install that? Is it on the Ubuntu CD or on this web site somewhere to download? And how do I run it once its downloaded?

Thx in advance.
Puffi

---

### Post by loell on 2006-11-18
```
sudo aptitude build-essential
```

you can run gcc

by typing gcc

---

### Post by loell on 2006-11-18
oh are you trying to compile nvidia drivers, you can install the binary if you like

[Nvidia driver installation]("http://https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29")

or better yet try [automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

---

### Post by taurus on 2006-11-18
> **loell said:**
> ```
sudo aptitude build-essential
```
It should be 

```
sudo aptitude install build-essential
```

---

### Post by loell on 2006-11-18
lol, a typo, sorry ;)

---

