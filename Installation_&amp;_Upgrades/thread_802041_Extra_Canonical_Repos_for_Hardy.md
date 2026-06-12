---
title: "Extra Canonical Repos for Hardy"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by pluckypigeon on 2008-05-21
I was browsing through the canonical repos on Firefox and saw that as well as Partner there are some more.

I found universe multiverse main and universe when trying to add them I did it wrong:

```
deb http://archive.canonical.com/ubuntu hardy partner main multiverse universe restricted

deb-src http://archive.canonical.com/ubuntu hardy partner main multiverse universe restricted
```

Does anyone know the correct way? Also should I be adding these?:confused:

---

### Post by zvacet on 2008-05-21
System>admin>software sources>check all under Ubuntu software and updates tab.Reload.

```
gksudo gedit /etc/apt/sources.list
```

your partner repository have to look like this

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 

sava file and close it.

```
sudo aptitude update
```

---

