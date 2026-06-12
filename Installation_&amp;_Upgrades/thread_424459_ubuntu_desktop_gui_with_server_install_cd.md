---
title: "ubuntu desktop gui with server install cd"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by nicker on 2007-04-26
So, I just had a successful install using the Feisty Fawn Server install cd.  I'm trying to install the ubuntu desktop on top of that as I was told I could do.
I was told I could use
sudo apt-get install ubuntu-desktop

and this would install the desktop for me.  I"m getting a message that says 

Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package ubuntu-desktop

Is it not on the cd?  How do I go about getting this to work?

Thanks in advance

---

### Post by kerry_s on 2007-04-26
make sure all your repos are on, you can comment out the cd you don't need it anymore.

sudo nano /etc/apt/sources.list

I'm not on ubuntu, so i can't post my sources.list.

---

### Post by zvacet on 2007-04-27
If you have server  Cd you don´t have desktop  on it.You will install it via network

```
sudo aptitude install ubuntu-desktop
```

---

