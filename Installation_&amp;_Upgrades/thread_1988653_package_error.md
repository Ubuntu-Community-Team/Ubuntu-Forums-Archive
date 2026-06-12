---
title: "package error"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2012-05-27
im getting this serious package error and i cant seem to figure out how to fix it, does anyone know a way or am i stuck reinstalling my OS? screenshot of the problem

---

### Post by wildmanne39 on 2012-05-28
Hi, please do:
```
gksu gedit /etc/apt/sources.list
```
Then remove [COLOR="Red"]nza [/COLOR]from line two save gedit close then:
```
sudo apt-get update
```
Thanks

---

### Post by TheRacerX on 2012-05-28
tried that couldn't find the nza in the source list at all

---

### Post by plucky on 2012-05-28
> **TheRacerX said:**
> tried that couldn't find the nza in the source list at all

Post output for ```
cat /etc/apt/sources.list.d/tiheum-equinox-precise.list
```

It should look like ```
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main 
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main
```


Good Luck

---

