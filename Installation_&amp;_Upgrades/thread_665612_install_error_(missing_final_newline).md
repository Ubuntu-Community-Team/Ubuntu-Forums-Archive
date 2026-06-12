---
title: "install error (missing final newline)"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by garymc1 on 2008-01-12
i am running feisty 7.04

after running fsck when i try to install programs i get this error in synaptic packages



E: /var/cache/apt/archives/exim4-config_4.63-11build1_all.deb: files list file for package `unrar' is missing final newline

please help
Thanks 
Gary

---

### Post by charleseddy on 2008-01-15
This generally happens after a filesystem becomes corrupt and has things moved around by fsck.  Here's a solution that should work:

1. sudo gedit /var/lib/dpkg/status
2. Delete the section for unrar.
3. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
4. sudo mkdir /var/lib/dpkg/info
5. sudo apt-get update
6. sudo apt-get -f install

Hope it helps.  Let us know.

---

