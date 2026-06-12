---
title: "Error on repository check"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2012-01-23
When updating the repository information I get the following error messga ecome up - can anyone tell me why and what I do about it?

[B]E: Encountered a section with no Package: header
E: Problem with MergeList 
/var/lib/apt/lists/mirror.as29550.net_archive.ubuntu.com_dists_oneiric-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/B]

---

### Post by plucky on 2012-01-23
> **bigtel said:**
> When updating the repository information I get the following error messga ecome up - can anyone tell me why and what I do about it?

[B]E: Encountered a section with no Package: header
E: Problem with MergeList 
/var/lib/apt/lists/mirror.as29550.net_archive.ubuntu.com_dists_oneiric-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/B]

From a terminal ```
sudo rm /var/lib/apt/lists/* -rf
``` then update again and see if you still get the same error.

Good luck

---

