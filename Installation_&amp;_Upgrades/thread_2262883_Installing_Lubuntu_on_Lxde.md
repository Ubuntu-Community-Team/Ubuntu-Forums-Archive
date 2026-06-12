---
title: "Installing Lubuntu on Lxde"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by cthang55 on 2015-01-27
I installed lxde 11 on my Samsung chromebook and it is very primitive looking. I would like to install lubuntu over lxde. Does anyone know if this is possible and how I should do it?

---

### Post by Bucky Ball on 2015-01-28
Welcome. Not knowing anything about lxde (it is not officially supported here) or what repositories it uses, I'm taking a guess, but in Ubuntu it would be:

```
sudo apt-get install lubuntu-desktop
```

You could also install lubuntu-desktop from whatever package manager lxde uses. You then log out, choose the Lubuntu session from the Sessions pop-up, and log in. You will be in Lubuntu.

Your other option, of course, is a clean install of Lubuntu 14.04. Good luck whichever way you go.

---

