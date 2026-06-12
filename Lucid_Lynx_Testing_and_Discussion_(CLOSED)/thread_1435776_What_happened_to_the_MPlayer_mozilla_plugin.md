---
title: "What happened to the MPlayer mozilla plugin"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2010-03-21
I can't install, or find the MPlayer mozilla plugin in synaptic. Anyone know why/how to get it? 

(screen attached)

---

### Post by collinp on 2010-03-21
You are probably looking for the package "gecko-mediaplayer", install it by executing the following command (in a terminal) and restarting Firefox:
```
sudo apt-get install gecko-mediaplayer
```

---

### Post by n0dix on 2010-03-21
> **myddewji13 said:**
> I can't install, or find the MPlayer mozilla plugin in synaptic. Anyone know why/how to get it? 

(screen attached)

Two things:
1. The image Synaptics, but you already knows that and check in the 'real' Synaptics ;)
2. I supposed you are using version 10.04 and the package isn't release to the repo.

---

### Post by mc4man on 2010-03-21
It's been replaced by gecko-mediaplayer

Depending on the sites you go to it may be superior, inferior or the same as the totem-mozilla plugin

(atm I prefer the totem plugin most of the time, switch off once and while - site specific

Note you should only have one or the other installed at one time.

(too bad browser plugin's  can't be set in alternatives

---

### Post by myddewji13 on 2010-03-21
The gecko-mediaplayer is awesome! Thank you!

---

