---
title: "Synaptic and Packages problem"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by SparkyDawg on 2005-06-05
I reinstalled Ubuntu a couple days ago, and when I try to install a package through synaptic or apt-get, it always wants me to put the ubuntu cd in. Why is that?

---

### Post by tread on 2005-06-05
If you have a good net connection, you can do the following:
sudo gedit /etc/apt/sources.list

and comment out the cdrom. This will prolly be the first line in the file.
After that, fire up synaptic and press reload.

---

