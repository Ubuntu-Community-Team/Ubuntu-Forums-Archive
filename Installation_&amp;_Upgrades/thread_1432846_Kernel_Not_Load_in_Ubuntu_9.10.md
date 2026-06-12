---
title: "Kernel Not Load in Ubuntu 9.10"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by Ranjithkumar on 2010-03-18
HI friends,
              I m new user for Ubuntu..I m using ubuntu for last 5 Months.I love very much and also i m spreading ubuntu community in my place.I have a problem now to use Ubuntu.When i on the ubuntu...Its says in grub kernel is not load...How i rectify this problem..Plz help me... Thanks for a million.

---

### Post by tom4everitt on 2010-03-18
If I understand your problem correctly you can not boot ubuntu, it hangs at grub. 

First try to boot from an earlier kernel (or failsafe mode). If you manage to get to a terminal run: 

sudo update-grub

which will probably fix it.



If you can't get to a terminal that way, follow this guide to restore grub:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

