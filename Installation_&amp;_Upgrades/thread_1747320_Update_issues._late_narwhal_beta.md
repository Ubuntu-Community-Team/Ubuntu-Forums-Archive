---
title: "Update issues. late narwhal beta"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by shadowofgrael on 2011-05-02
I am using 11.4 Beta

everything has been working until very recently. (coincidentally around the time the final release) now whenever i use apt-get i receive these errors:
```
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 2,460 kB in 1min 30s (27.3 kB/s)                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```This example is from apt-get update.
It was recommended in a different thread that this problem be solved by:
```
mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main* /<Memorable Location> && apt-get update 
```running both commands as root did not solve the problem.
Any ideas would be great.

i cannot use synaptic etc. via gui due to similar errors

---

### Post by shadowofgrael on 2011-05-03
self bump
One day has passed and no responses

---

### Post by shadowofgrael on 2011-05-03
Never mind. The problem was solved after a more liberal purge of the .../lists directory (sudo rm -rf *)

---

