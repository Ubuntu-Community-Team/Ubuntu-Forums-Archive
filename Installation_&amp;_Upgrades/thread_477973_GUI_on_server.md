---
title: "GUI on server?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by wizekid on 2007-06-18
hello guys  what are the commands for me to install a GUI instaed of a command line  on a ubuntu server ed? thanks

---

### Post by yabbadabbadont on 2007-06-18
If you want the full Ubuntu graphical desktop setup, then install the ubuntu-desktop package.  (using whichever package manager you like)

---

### Post by scrooge_74 on 2007-06-18
sudo apt-get install xubuntu-desktop

sudo apt-get install icewm  if you want something lighter

---

### Post by zvacet on 2007-06-19
```
sudo aptitude install ubuntu-desktop
```

or if you prefer KDE

```
sudo aptitude install kubuntu-desktop
```

---

### Post by nerrick on 2007-07-06
> **scrooge_74 said:**
> sudo apt-get install xubuntu-desktop

sudo apt-get install icewm  if you want something lighter

> **zvacet said:**
> ```
sudo aptitude install ubuntu-desktop
```

or if you prefer KDE

```
sudo aptitude install kubuntu-desktop
```

I have had no luck with any of these commands. Any Ideas?

---

### Post by az on 2007-07-06
Are you connected to the internet?

As well, I would suggest you install the desktop kernel

sudo apt-get install linux-image-generic linux-server-

so you can do:

sudo apt-get install ubuntu-desktop linux-image-server linux-server-

---

