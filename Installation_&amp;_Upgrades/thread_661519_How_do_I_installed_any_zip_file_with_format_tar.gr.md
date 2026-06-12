---
title: "How do I installed any zip file with format tar.gr ?"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by picard12 on 2008-01-08
How do I installed any zip file with format tar.gz ?

---

### Post by erfahren on 2008-01-08
> **picard12 said:**
> How do I installed any zip file with format tar.gr ?
are you sure it's not "tar.gz" ? Is it a program or a theme (of some kind)?

if it's a program then it is the source code and may need to be compiled - first search Synaptic and make sure the program isn't already available - if it doesn't we can give you links, tips and such to help you compile it. - include a link to where you got it if you would.

---

### Post by picard12 on 2008-01-08
> **erfahren said:**
> are you sure it's not "tar.gz" ? Is it a program or a theme (of some kind)?

if it's a program then it is the source code and may need to be compiled - first search Synaptic and make sure the program isn't already available - if it doesn't we can give you links, tips and such to help you compile it. - include a link to where you got it if you would.

ok. it is the "tar.gz" file format. I want to install flash plugin for firefox and Nero burner software. The file is zip. My PC has Fedora now. 

I still haven't figure out how to partition my HD to accommodate Ubuntu desktop.:( 
Fedora looks different. There is no gpart software for me to partition this HD. 

HELP ??

---

### Post by erfahren on 2008-01-08
the Flash plugin has its own installer - you can just uncompress the archive (may be able to just right-click and "Extract" - or else:
```

tar xvzf package-name.tar.gz

```
then change directory (cd) into it and run like (look inside it or list (ls) to find the name):
```

sudo ./name-of-installer-script

```

The Nero I don't know about

GParted probably isn't installed by default - check Fedora's rpositories - or: you can get it or its LiveCD from here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

(The Ubuntu LiveCD has GParted on it).

---

