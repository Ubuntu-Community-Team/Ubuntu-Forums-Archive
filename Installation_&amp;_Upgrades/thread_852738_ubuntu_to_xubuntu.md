---
title: "ubuntu to xubuntu"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Zopiac on 2008-07-07
one of my computers is very slow, and is running ubuntu HH 32bit. can i switch to xubuntu using a terminal command, package, etc.? i dont have the time to order and wait for cds, i cant burn cds, and i have no one that has even heard of ubuntu near me, let alone who has an xubuntu disk i can borrow :\ what do i do?

---

### Post by iaculallad on 2008-07-07
Using the terminal:

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install xubuntu-desktop

```

Then choose the "xfce-session" or similar selection from the GDM login manager.

---

