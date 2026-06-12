---
title: "internet problem"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by dinamic1 on 2010-03-13
hi guys.. i'm on ubuntu 9.10 and i have a ppoe internet connection, because i coudn't connect to internet through the network manager.. i've use sudo pppoeconf 

the thing is that the connection is being made but the only thing that works is google.ro

---

### Post by YannBuntu on 2010-03-17
Hi,
if you can read French, follow this: [http://doc.ubuntu-fr.org/tutoriel/karmic_internet_problemes](http://doc.ubuntu-fr.org/tutoriel/karmic_internet_problemes)

If not, add this repository to your Software sources : ppa:network-manager/trunk

Then update your packages.

Then run this command in a Terminal to use back NetworkManager: sudo rm /etc/network/interfaces

If everything is ok, remove the PPA from your sources.

---

