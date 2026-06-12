---
title: "Installing samba4 on Jaunty"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by glauco.b on 2009-03-01
Hello all

I'm just trying to install the samba4 package on my fresh jaunty setup.

I ran into the following problem:
1. samba4 depends on python-samba (v4.something)
2. python-samba depends on a strange version of python (>2.5 and <2.6)
3. the python version installed on jaunty is 2.6.1, so the package won't install
4. AFAIK there is NO way to tell apt to ignore dependencies
FINAL. no samba4 installed on my system

I see a dependency problem here... :confused: I'm using ONLY the official ubuntu repositories

Anyone tried to get samba4 working on jaunty? Is this only my fault?

---

### Post by IanW on 2009-03-01
See the sticky in this forum entitled ["Heads up: Jaunty upgrades will be broken](http://ubuntuforums.org/showthread.php?t=1082102)

Short version - The developers are migrating us to Python 2.6, so EVERYTHING python-based needs rebuilding, this will take a day or two.

---

### Post by glauco.b on 2009-03-02
Thank you

I'll wait then... :popcorn:

---

