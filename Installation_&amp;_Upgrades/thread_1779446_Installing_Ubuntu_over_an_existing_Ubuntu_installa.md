---
title: "Installing Ubuntu over an existing Ubuntu installation"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by padfootpak on 2011-06-10
I am trying to install Lucid Lynx over Maverick Meerkat. What is the correct way to do that? I mean, do I have to completely format my Hard disk. I do not want to do that. I have Windows 7 also installed as dual boot.

---

### Post by akand074 on 2011-06-10
> **padfootpak said:**
> I am trying to install Lucid Lynx over Maverick Meerkat. What is the correct way to do that? I mean, do I have to completely format my Hard disk. I do not want to do that. I have Windows 7 also installed as dual boot.

Just format your Ubuntu partition and install it over that partition. If you used an autoinstaller before, then just use a partition manager (gparted) and delete all the Ubuntu partitions leaving unallocated space, then the autoinstaller will automatically install Ubuntu in that unallocated space. Otherwise if you did a manual install from the start, then you should know what to do after deleting the Ubuntu partitions. Do not touch your Windows partition.

---

