---
title: "watching a windows wma file in Xubuntu?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2008-04-03
Xubuntu 7.10 starndard install on an older machine.  What do I install or modify to watch a wma file?

thanks...

---

### Post by pseudo-random on 2008-04-03
You need the medibuntu package.

---

### Post by shultzjr on 2008-04-03
Do I just do a "sudo apt-get install mediubuntu"?

---

### Post by Dynaflow on 2008-04-04
In the terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install w32codecs
```

If you happen to have a DVD player on that computer that you'd like to have fully enabled, Medibuntu is the place to go for that software too.

```
sudo apt-get install libdvdcss2
```

---

