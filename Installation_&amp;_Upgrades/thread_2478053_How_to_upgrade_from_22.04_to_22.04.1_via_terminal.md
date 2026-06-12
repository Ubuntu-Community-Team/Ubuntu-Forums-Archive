---
title: "How to upgrade from 22.04 to 22.04.1 via terminal?"
date: 2022-08-15
forum: Installation &amp; Upgrades
---

### Post by schwim-dandy on 2022-08-15
Hello there folks!

I have a server install of 22.04 that I use for my personal desktop and saw that .1 had been released.  I did an upgrade via terminal and apt-get didn't notify me of a new release.  How to I upgrade to .1 via terminal?

Thanks for your time!

---

### Post by mikewhatever on 2022-08-15
Have you tried <lsb_release -d>?

---

### Post by deadflowr on 2022-08-15
```
sudo apt update
sudo apt full-upgrade
```
that is all you need since it's the same release.

---

