---
title: "Can I reset Ubuntu without doing a full reinstall?"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by hwyckoff on 2012-09-09
A few days ago I installed Ubuntu 12 as a dual-boot with Windows 7 on an AMD64 computer.  In the process of learning how to customize Ubuntu so I can run the programs I need, I noticed that some of the procedures I discovered in forums or on webpages were total failures, leaving a trail of incomplete installs or unneeded and orphaned dependencies.  

One way I know to clean it up is to do a full reinstall of Ubuntu 12, but I want to avoid that if possible.  One reason is that I don't want to reinvent some of the successful customizations I did manage to perform.  Is there some kind of cleanup command I can use in Terminal or a graphical interface to clean up unneeded or orphaned dependencies?

Any hints or solutions would be greatly appreciated.  Thank you.

---

### Post by Bashing-om on 2012-09-09
hwyckoff; Hi ! Welcome to the forum;

cleanups: run these in terminal (ctl+alt+t)
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

```the use of sudo (super user) requires your pass word, will get no echo at all back to the screen (security reasons).

good reading material:
```

man sudo
man apt-get

```A desire of mine is that you enjoy ubuntu, have questions, ask ![INDENT]kindest regards <==BDQ
[/INDENT]

---

### Post by leclerc65 on 2012-09-09
I cloned the system (using Clonezilla) occasionally, and before any drastic modification to the system. I avoid keeping data in the home partition. It takes 3 minutes to clone the '/' partition and about 1/2 hr for the '/home' (due to .thunderbird and vboxed XP).

---

### Post by hwyckoff on 2012-09-10
> **Bashing-om said:**
> hwyckoff; Hi ! Welcome to the forum;

cleanups: run these in terminal (ctl+alt+t)
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

```the use of sudo (super user) requires your pass word, will get no echo at all back to the screen (security reasons).

good reading material:
```

man sudo
man apt-get

```A desire of mine is that you enjoy ubuntu, have questions, ask ![INDENT]kindest regards <==BDQ
[/INDENT]
This was exactly what I had in mind. Thank you very much!

---

