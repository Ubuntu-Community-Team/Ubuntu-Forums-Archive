---
title: "Installed Lucid alongside Meego, resized partitions and now 3 Ubuntu FS show in grub"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by Tanvile on 2012-01-06
Installed Lucid alongside Meego, resized partitions and now 3 Ubuntu FS show up in grub, each having a separate (safe mode) load link(?), yet all of them load the same physical FS.

Any ideas how to fix this? Also, there is some Memory test 86x - what's that? ;)

---

### Post by zvacet on 2012-01-07
Yo have few different kernels installed and each of them have safe mode ( I think it is recovery mode but we understand each other).If you want to remove some of them first be sure that latest ( with higher number ) is working correctly.If it does go to the **synaptic package manager** and type in search box **linux-image**.You will see all installed kernels.Remove all of them except one with higher number.After that do the same with **linux-headers**.

---

