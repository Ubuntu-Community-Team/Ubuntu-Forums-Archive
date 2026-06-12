---
title: "Package installation hangs system"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by diafanos on 2008-07-29
I use Hardy and when I'm trying to install a package (using synaptic or CLI), my system hangs for some seconds, while installation is in progress.
It's not such a big problem, but is a little annoying and I had not experienced a similar case with previous ubuntu versions.

Is there any workaround?
My specs: Core2Duo @2.13, 1GB RAM

Is there any way to force synaptic to use only one of the two processors, so that my system run without hangs?

Thanx.

---

### Post by coffeecat on 2008-07-29
You could run apt-get with nice, thus:

```
sudo nice -n NICENESS apt-get PACKAGE
```... where NICENESS is an integer between -20 and 19. See man nice.

I've never needed to do this myself, but it should work. I have no idea what degree of niceness you need to select. You'll have to experiment. This only affects scheduling - it doesn't allocate one processor only to apt-get - but it should have the effect you want.

---

### Post by diafanos on 2008-07-29
thanks a lot coffeecat!

I'll follow your advice in the next update...

---

