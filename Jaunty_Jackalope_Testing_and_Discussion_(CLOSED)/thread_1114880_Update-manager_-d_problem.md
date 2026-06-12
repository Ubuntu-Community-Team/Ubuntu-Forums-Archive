---
title: "Update-manager -d problem"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aethralis on 2009-04-03
I tried to upgrade to jaunty (from intrepid)  via "update-manager -d" and that did not do the trick. "do-release-upgrade -d" gives: Checking for a new ubuntu release. No new release found. I reinstalled update-manager-core and even installed update-manager from intrepid proposed, but that did not help either. 

There is an old bug ([https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/211978/](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/211978/)) concerning similar problems. Is anyone else affected?

---

### Post by BGFG on 2009-04-03
try :
```

sudo aptitude update

```
then 
```

sudo aptitude upgrade

```
works better than update manager and may fix it.

---

### Post by hotstovejer on 2009-04-03
You also might want to check that in Software Sources, you have it set to look for normal releases, vs long term ones, or never. [ATTACH]108506[/ATTACH]

Let us know if that works!

Thanks!

Jeremy

---

### Post by aethralis on 2009-04-03
Normal releases is checked. aptitude upgrade did not work. Changed also the software sources to ubuntu main, and that did not help either.

---

### Post by wgrant on 2009-04-03
Upgrades are currently disabled due to some breakage. Give it a day or two and try again.

---

### Post by aethralis on 2009-04-03
Thanks, I guess that explains it :)

---

### Post by BGFG on 2009-04-03
because I was stumped! :) thanks wgrant

---

### Post by rburkartjo on 2009-04-03
wgrant tks for the heads up

---

