---
title: "Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise-"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by gosi1977 on 2012-03-24
need help with the following error message 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by wildmanne39 on 2012-03-24
Hi, try this:
```
sudo rm /var/lib/apt/lists/* -vf
```

The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```
is the 12.04 beta?
Thanks

---

### Post by RememberWhenItRained on 2012-05-02
i had the same problem (not sure what caused it) and your solution worked. Thank you.

---

### Post by Bryanjpg on 2012-09-27
This helped solve my similar problem as well. Thanks!

---

