---
title: "[SOLVED] how to install a tar.bz2 file"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by swotie on 2008-10-31
I have downloaded "flock" browser. it is a "tar.bz2" ... how do I install this program i hardy desktop


flock_afc0600546A2B78-2.0.en-US.linux-i686.tar.bz2

---

### Post by Idefix82 on 2008-10-31
Instead of downloading tar balls you can just add the relevant repository to your package manager and let it handle the rest. This way you will also be notified about updates:
```
gksudo gedit /etc/apt/sources.list
```
opens a text editor with the file which contains information about your repositories. Add the lines
```
deb http://www.salatti.net/repo/ hardy-salatti main contrib non-free
deb-src http://www.salatti.net/repo/ hardy-salatti main contrib non-free
```
save and exit. Now just do
```
sudo apt-get update
```
and
```
sudo apt-get install flock
```

---

