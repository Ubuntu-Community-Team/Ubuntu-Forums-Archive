---
title: "Error is occurring in initiation of updates,"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by mahboob218 on 2013-07-06
hi everyone 

i have ubuntu 12.04 and the following error is occurring before the updates get install ,,

''E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.''


how i can fix this problem 

help me

---

### Post by fantab on 2013-07-06
From Terminal run:
```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by mahboob218 on 2013-07-06
thanks   ''fantab''  your idea was helpful

---

