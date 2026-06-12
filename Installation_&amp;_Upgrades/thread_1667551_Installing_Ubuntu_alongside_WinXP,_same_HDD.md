---
title: "Installing Ubuntu alongside WinXP, same HDD?"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Rivers48 on 2011-01-15
Hey,

So i want to install the Ubuntu netbook remix on my EeePC 100H alongside WinXP. There is a 160gb HDD in there and its split into two even partitions. I want to know if i can install Ubuntu on the same HDD there but on a different partition? so Windows is on /dev/sda1 and i want Ubuntu on /dev/sda2? I select the partition and click install but it says "no root file system is defined. Please define this from the partitioning menu."

Any thoughts or help would be good,

Thanks.

---

### Post by presence1960 on 2011-01-15
Highlight sda2 and click change. Tick the format box, use as ext4, and mount point set as /.

Now you will be able to proceed.

---

### Post by Rivers48 on 2011-01-15
Thanks, worked a treat!

---

