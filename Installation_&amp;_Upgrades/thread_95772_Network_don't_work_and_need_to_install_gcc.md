---
title: "Network don't work and need to install gcc"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by Helios89 on 2005-11-27
Hi all. I've just installed Kubuntu from my CD. My ethernet modem doesn't work, i need rp-pppoe but it needs to be compiled. I haven't gcc installed and i don't know how to install it from cd.. Can you help me?

---

### Post by Helios89 on 2005-11-27
Sorry for my bad english, too!

---

### Post by schdefan on 2005-11-27
Hi!
To compile soure code you need gcc. Install the package build-essential to get te compiler. Maybe you will be fine with the package pppoe.
schdefan

---

### Post by Helios89 on 2005-11-27
i've fixed that. I did

```
apt-get install gcc
```


but i have no idea where it took gcc... now when i compile pppoe it tells me that gcc cannot make executables! 

How to continue?

---

### Post by Corvillus on 2005-11-27
You have to use
```
sudo apt-get install build-essential
```
to get all of the basic libraries and tools for building applications from source

---

