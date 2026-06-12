---
title: "Crebs and PPA issue, upgraded installation"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by MavisCruet on 2011-10-22
Hello,

I have an issue on my friend's laptop where I ran an upgraded install (I know) and as there's no more Synaptic, and the application Crebs is no longer supported, it keeps giving errors on the system update as well as a warning triangle about it.

Having looked through it, it is just the crebs stuff that is generating these, but I can't figure out how to get the repositories back to a default setting, or to delete the various files in question as they're locked to root.

Has anyone else had this issue, and if so, how have you overcome it, assuming you have?

Cheers, 

Mavis

---

### Post by zvacet on 2011-10-22
Yes synaptic doesn´t come preinstalled witch is IMHO strange.So you will have to install it 

```
sudo apt-get install synaptic
```

If some PPA give you trouble remove it from source list from synaptic>repositories and uncheck it.Refresh synaptic and mark all updates.You should be fine.

---

### Post by MavisCruet on 2011-10-22
That was an impressively simple solution, I shall try it, thank you

---

