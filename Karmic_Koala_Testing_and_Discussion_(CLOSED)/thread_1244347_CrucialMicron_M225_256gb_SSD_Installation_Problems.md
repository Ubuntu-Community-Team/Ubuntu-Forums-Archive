---
title: "Crucial/Micron M225 256gb SSD Installation Problems"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rachaelb on 2009-08-19
Have tried in vain to install Kubuntu on my new Crucial M225 256gb SSD

The actual size of the drive (according to GParted, Windows [sorry!] and Crucial themselves) is 238.47gb... however, the install disc seems to be trying to partition to the reported 256.1gb

These discs will NOT install:

Kubuntu 9.10 alpha 4 Live CD
Kubuntu 9.10 alpha 4 alternate CD
Kubuntu 9.10 netbook remix
Ubuntu 9.10 UNR
Ubuntu 9.04 UNR

However, it is possible to install using Kubuntu 9.04 alternate PROVIDING the installation option chosen is either "guided using LVM" or "guided using LVM with encryption". Any other partitioning does not work. Manual partitioning to duplicate the LV structure of the guided process also does not work

OpenSUSE 11.1 live CD will only install if the LVM option is chosen. A regular install fails here as well.

I think this is a problem.

Have registered it on launchpad

---

