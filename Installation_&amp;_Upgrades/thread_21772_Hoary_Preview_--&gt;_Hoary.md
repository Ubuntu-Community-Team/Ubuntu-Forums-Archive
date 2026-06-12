---
title: "Hoary Preview --&gt; Hoary"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by kb00heda on 2005-03-23
Hopefully a quick and easy question:

Will it be enough just to upgrade the preview version on Hoary, e.g., by using apt, to get the "real" Hoary once it gets released? I would think so? (That would save the time it takes to make a clean installation.)

/David

---

### Post by ubuntu_demon on 2005-03-24
[QUOTE=kb00heda]Hopefully a quick and easy question:

Will it be enough just to upgrade the preview version on Hoary, e.g., by using apt, to get the "real" Hoary once it gets released? I would think so? (That would save the time it takes to make a clean installation.)

/David[/QUOTE]
 just do :

sudo apt-get ubuntu-base ubuntu-desktop (to make sure you still have them)
sudo apt-get dist-upgrade

and you're finished :)

---

### Post by kb00heda on 2005-03-24
Sounds great!   :)

---

### Post by jdong on 2005-03-24
Actually, you only need to do the periodical system update through "apt-get dist-upgrade". Hoary Preview will automatically turn into Hoary when it's released.

---

