---
title: "cannot upgrade to 13.10"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by damicogiuseppe77-2 on 2014-01-13
Hi when I try to upgrade I get this error:

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
I am running ubuntu 13.04 never had this problem before, what should I do? I would like to avoid a new installation

---

### Post by monkeybrain20122 on 2014-01-13
Just backup your data and do a clean install. Upgrade takes a long time and it is not reliable especially if your system has been modified (ppa, third party apps, proprietary graphic card etc) Take a look at the threads on these forums, a large number of problems are caused by bad upgrades.

---

### Post by Bucky Ball on 2014-01-13
Try switching off all third-party repositories and checking how much room you have on the partition you are trying to upgrade. It is not mentioned but this error also occurs when there is not enough room to do the upgrade. The upgrade needs some headroom to hold packages for installation (the data is later deleted). If you don't have enough headroom the upgrade will stall.

---

