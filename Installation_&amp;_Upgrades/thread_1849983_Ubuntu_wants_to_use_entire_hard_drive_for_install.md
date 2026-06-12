---
title: "Ubuntu wants to use entire hard drive for install?"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by Sandy000 on 2011-09-25
My Windows Xp recently had a huge problem. 
I've tried the recovery option but Windows Xp won't boot says missing or corrupt files. 
Any way my daughter found Ubuntu for me to try and by using the cd she created I am able to get online. 
So I decided that I wanted to use Ubuntu. I went to do the install but it wants to erase the disk and use the entire 250.1 GB ? I stopped the install because I'm confused as to why it would need to use the entire disk and if it could even function if it needs that much space? It also mentioned 2 partitions would be deleted, is that safe? Thanks for any help that you can give.

---

### Post by zvacet on 2011-09-25
Run Ubuntu live cd and make new partition with Gparted.You will probably have to shrink one Windows partition to make space for Ubuntu.When you are done with that start installing ubuntu and on partitioning stage select manual way so you can select your free space to install Ubuntu on it.

---

### Post by OpenJacob on 2011-09-25
Ubuntu is asking you to format the drive so that it can install. It is not asking you to install 250Gigs of software.

---

### Post by Hakunka-Matata on 2011-09-25
Hi, Welcome to the forums,

In order to possibly help we need to know more about the current partitioning of your hard drive(s).  Please run these commands and post the results.
```
sudo fdisk -l && sudo sfdisk -luS
```

---

