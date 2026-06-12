---
title: "Synaptic cannot start"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by yndesai on 2011-09-02
Following error is seen when I start up the synaptic. 
I have just installed 11.04 and was adding few of my favorite softwares.

This ocured after I tried to installed xpaint which did not install and now I am
not able to start the synaptic. 

```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fIN
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


```Thanks in advance

YNDESAI

---

### Post by Rubi1200 on 2011-09-02
Hi,
open a terminal and copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first one removes corrupted package lists, the second one refreshes them.

---

### Post by yndesai on 2011-09-04
Thank you my issue is now resolved.

Wanted to know how did this err criped in. . 

Thanks once again

---

### Post by Rubi1200 on 2011-09-04
Glad things worked out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

