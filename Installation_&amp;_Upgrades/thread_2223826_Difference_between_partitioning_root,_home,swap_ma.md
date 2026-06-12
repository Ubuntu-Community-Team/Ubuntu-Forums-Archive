---
title: "Difference between partitioning root, home,swap manually and not partitioning"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by pranish on 2014-05-13
While installing ubuntu, we have to manually provide partition to home, root, swap , etc. Ubuntu can be installed without manually partitioning also. Whats the dirrefence between that and which one is better.
Thank you

---

### Post by sudodus on 2014-05-13
It depends ...

The standard automatic installation will give you one root partiiton and one swap partition. ***If you want to use the whole drive***, that is simple and a very good alternative.

The 'install alongside' alternatives are tricky. Some people have misunderstood them and overwritten what they wanted to keep. So for all instances except using the whole drive, I suggest that you select '***Something else***' at the partitioning page and select partitions manually.

It is easier to do the partitioning with ***gparted*** (which comes with the Ubuntu family desktop installer iso files), and only select partitions with the installer.

---

