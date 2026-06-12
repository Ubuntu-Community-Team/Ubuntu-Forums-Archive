---
title: "install frozen?"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2008-03-18
every time I try to install ubuntu ( I tried to install several times) the installer freezes when it starts to repartition the disk. and i have to hold down the power button on the cpu to turn the computer off. Does anyone out there have this problem?
whats the solution?

edit: the live cd works fine without installing.

---

### Post by housam on 2008-03-18
Download and burn[[COLOR="Red"]_ the newer version of Gparted _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")and boot from this CD to partition your HDD manually . and during the installation process assign the partitions manually. ( you need at least 2 partitions - one as a root ( / ) ext3 format and the other is for the swap ( 1 to 2 GB is ok ))

---

### Post by Tomatz on 2008-03-18
Or download the "alternate 7.10 .iso" it is a text based installer.  If you are using older hardware the problem is probably that you are running out of ram with the live cd.

---

