---
title: "&quot;Problems with merge list&quot; bug in update manager"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by brougzog on 2014-05-30
Hi, 
First time posting in here, after 3 years of ubuntu and a lot of successful copy/pasting for most problems

But this time, despite a bit of search, I did not find any suitable response to this one, 

using the latest version, 

here is the evidence:

> E:Encountered a section with no Package: header, E:Problem with  MergeList  /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-fr,

Thanx & sorry if already adressed, 

Brougzog

---

### Post by matt_symes on 2014-05-30
Hi

Open a terminal and try  this.
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

It will delete all your existing package lists and then get them again.

Kind regards

---

