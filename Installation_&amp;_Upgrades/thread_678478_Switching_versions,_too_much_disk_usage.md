---
title: "Switching versions, too much disk usage"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by ChrisMP1 on 2008-01-25
I initially installed Xubuntu (low RAM). I've upgraded my RAM and I switched around a bit.

I tried Kubuntu (apt-get install kubuntu-desktop) and finally settled on regular Ubuntu. I removed the xubuntu-desktop package, the kubuntu-desktop package, and everything I could find in Synaptic remotely related to XFCE or KDE, but my disk is still too full.

```
$ du -shx /
2.4G    /
```

With -x, that doesn't include my separate-partition /home, and the only other packages I have installed are AbiWord, Gnumeric, and gdesklets. I've use pure Ubuntu with these same packages installed, and the disk usage was around 1.9 GB. Any ideas on which packages I still might have to remove?

(It can't be config files either; I used apt-get purge, and 512 MB is a *lot* for config files anyway.)

---

### Post by mouseboyx on 2008-01-25
try

sudo apt-get clean it should delete all of the package files that you don't really need.

---

### Post by ChrisMP1 on 2008-01-26
I did apt-get clean.

---

