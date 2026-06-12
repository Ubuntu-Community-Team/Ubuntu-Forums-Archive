---
title: "unable to open software center"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by singhsudeep on 2011-06-05
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.



please help

---

### Post by matt_symes on 2011-06-05
Hi

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```Enter your password. It will not echoed to the screen. This is normal.

Then type

```
sudo apt-get update
```Kind regards

---

