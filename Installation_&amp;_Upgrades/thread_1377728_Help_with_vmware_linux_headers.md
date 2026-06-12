---
title: "Help with vmware/ linux headers"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by co264510 on 2010-01-10
hi i am trying to install vmware server on my ubuntu 8.04 system with gnome setup - i have followed some guides but am coming unstuck when having to download necessary packages

its says sudo apt-get install linux-headers-`uname -r` build-essential xinetd

which i type and get unknown error

so then i type uname -r and it displays

2.6.28.4-xxxx-std-ipv4-32 - what does this mean and what package to i need?

i have then tried sudo apt-get linux-headers-2.6.28.4-xxxx-std-ipv4-32 build-essential xinetd

but i still get errors, can anyone help thanks

---

### Post by SecretCode on 2010-01-11
It might be better if you posted the **exact** error you're getting (copy and paste).

2.6.28.4-xxxx-std-ipv4-32 is an odd result from uname -r - is this a special kernel? You'll need the headers for it, otherwise you won't be able to compile anything.

Also post the output of
```
sudo aptitude search linux-headers-
```

---

