---
title: "Update manager pop-up warning -- how to resolve?"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by fursulin on 2006-11-30
Newbie alert, newbie allert! :mrgreen:

> 
W: Duplicate sources.list entry http://au.archive.ubuntu.comdapper/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
Is this something serious or I shoudln't worry too much?
Could it be (easily) fixed? :-k

Tx

---

### Post by apjone on 2006-11-30
looks like [http://au.archive.ubuntu.comdapper/universe](http://au.archive.ubuntu.comdapper/universe) appears twice in your /etc/apt/sources.list. all you need to do is 
```

sudo gedit /etc/apt/sources.list

```
and remove the dupplicate entry and run
```

sudo apt-get update

```
and then the error should dissappear.

---

