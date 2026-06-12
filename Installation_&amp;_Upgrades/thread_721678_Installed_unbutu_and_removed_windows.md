---
title: "Installed unbutu and removed windows"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Roosta21 on 2008-03-11
Hi

I installed unbutu on a new machine and it removed the windows partition, this was a mistake.. Is it possible to install windows again with removing ubuntu?

---

### Post by Pumalite on 2008-03-11
Do you mean 'without' removing Ubuntu? If that is the case, the answer is possibly yes. Get Gparted Live CD and shrink your Ubuntu partition after backing up everything. Also your Windows might be there and you are just not able to boot it.
Post:
sudo fdisk -lu

---

