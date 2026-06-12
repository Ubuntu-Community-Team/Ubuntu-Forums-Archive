---
title: "Separate boot partition for the kernel"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by penguinland on 2006-10-29
I've been running Gentoo for several years, and am considering switching to Xubuntu. One thing I really liked about Gentoo is that my kernel had its own partition on my hard drive. Consequently, I could trash my entire file system and still have no troubles booting up. 

Unfortunately, I can't find any Ubuntu user who has done this. Does anyone know how to do it on Ubuntu? I already have my hard drive partitioned; I imagine that all I need to do is mount the extra partition before bootstrapping the OS. However, I've heard that the Ubuntu installation process is so easy and automatic that I don't need to concern myself about things like bootstrapping, even if I want to. Any thoughts?

Thanks for the help!

---

### Post by DJ Wings on 2006-10-29
At the last step of installation, it gives you a list of all the partitions, and where they'll be mounted. If you mean just a /boot partition, type in "/boot" where it says "/media/hdXX" next to your partition.
PS: Xubuntu is underrated.

---

### Post by penguinland on 2006-10-29
Sweet, dude. Thanks!

---

