---
title: "How to avoid install documentation packages?"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by rubenqba on 2010-05-14
Hello to all community.
Is there any way to prevent the installation of packages that contain documentation in Ubuntu?
I'm a developer who live in Cuba and here the connection is so slow that many times, it is impossible to keep the system updated and would be great to know how to avoid downloading the documentation packages, which are usually the largest. Something like it is on Gentoo, with the variable USE="-doc".

---

### Post by davidmohammed on 2010-05-14
from synaptic package manager - search for localepurge.  That should reduce the amount of documentation to the minimum - beware of the warning though in the description.

---

### Post by rubenqba on 2010-05-14
> **davidmohammed said:**
> from synaptic package manager - search for localepurge.  That should reduce the amount of documentation to the minimum - beware of the warning though in the description.

This is a  solution, but it only works to clean packages already installed. What I want to  solve it, not install the documentation.
For example I would like to install the libboost but not having  to download libboost-doc.

---

### Post by davidmohammed on 2010-05-14
If you find an answer then great - however, as far as I understand debian packaging you have to download all related packages otherwise the overall package thinks its broken.

---

### Post by rubenqba on 2010-05-14
It's a  shame. Ok, thanks for the help.

---

