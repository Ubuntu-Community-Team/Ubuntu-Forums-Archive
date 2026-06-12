---
title: "upgrade failed"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by katiad on 2005-10-18
Got these errors after using Synaptic to upgrade following the instructions listed in the release notes.

E: /var/cache/apt/archives/liburi-perl_1.35-1_all.deb:  cannot access archive: No such file or directory
E: /var/cache/apt/archives/libhtml-parser-perl_3.45-2_i386.deb:  cannot access archive: No such file or directory
E: /var/cache/apt/archives/libwww-perl_5.803-4_all.deb:  cannot access archive: No such file or directory


The entire upgrade then failed. What can I do?

---

### Post by Murgle on 2005-10-18
can you go into your /etc/apt/sources.list and change remove the us. infrom of archive.ubuntu.com if it is there, then reload your packages then try again

type 'sudo gedit /etc/apt/sources.list' to get to your sources.list

---

