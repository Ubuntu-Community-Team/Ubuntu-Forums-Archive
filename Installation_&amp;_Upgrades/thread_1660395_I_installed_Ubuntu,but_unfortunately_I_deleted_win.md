---
title: "I installed Ubuntu,but unfortunately I deleted windows"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Love-computers on 2011-01-05
Hello gys,I got a problem.I created partition (20 GB) to install my Ubuntu 10.10.But I installed it on wrong partition,and I deleted my Windows.How to create partitions on Ubuntu(and also which size schould be the partitions) to install windows again?I need windows cuz in the school,we use windows instead of Ubuntu.

---

### Post by rory526 on 2011-01-05
Use a program called gparted. Might be best run from a ubuntu live cd.

---

### Post by Love-computers on 2011-01-05
Well,thanks.I'll tell you what I've done :)

---

### Post by Rubi1200 on 2011-01-05
Hi and welcome to the forums :-)

Some advice:

Use the Ubuntu CD to boot the computer, choosing to try not install

At the desktop, go to Applications > Accessories > Terminal

Run this command and copy/paste the output here so we can advise you better on how to partition your drive:
```
sudo parted -l
```

(lowercase L not 1)

---

