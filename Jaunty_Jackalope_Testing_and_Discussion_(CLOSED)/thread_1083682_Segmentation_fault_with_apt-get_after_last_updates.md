---
title: "Segmentation fault with apt-get after last updates!"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-03-01
After last set of update, including packages related to launchpad integration, apt was broken.

running apt-get update download package data, then spits:
Segmentation fault (core dumped)

Running apt-get dist-upgrade yields immediate segmentation fault.

EDIT:
Fortunately, there is a solution:
> sudo rm -f /var/cache/apt/*.bin
sudo apt-get update

---

