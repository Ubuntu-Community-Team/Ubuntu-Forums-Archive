---
title: "Find non-meta-package packages"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by h.aling on 2007-03-25
Dear Forum,

My current PC was originally installed with a beta version of Dapper and has had dist-upgrades to Edgy and Feisty(beta).

During these upgrades, the meta packages containing the 'default' software probably have changed a lot, leaving a lot of unused programs on my PC.

I have use 'deborphan' to find stale libraries, but is there a way to find all packages that do not belong to ubuntu-standard, xubuntu-desktop, etc meta packages?

-tnx-

Harold.

---

### Post by zvacet on 2007-03-26
All downloads via synaptic or apt-get are in var/cache/apt/archives .since you did many upgrades it is very possible that you have number of packages you don´t use any more(old versions).You can clean with
```
sudo apt-get autoclean
```

Just to satisfied your couriosity go to the var/cache/apt/archives and in edit pick select all.In the status bar you will see how many MB or GB of space is used.Do the same after cleaning and you will see the diference.Don´t be afraid to clean,it is safe and desireble thing to do.that way you will have only latest versions of your programs,and that is what you want.

---

