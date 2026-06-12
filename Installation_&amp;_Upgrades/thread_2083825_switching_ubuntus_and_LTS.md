---
title: "switching ubuntus and LTS"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by juniper1982 on 2012-11-13
Hello,

I did a network install whereby I downloaded a linux kernel with a initrd image and booted them with an existing ubuntu installation.  I then picked lubuntu-desktop when I was asked to choose various software package.  this is all 12.04.  I then read that lubuntu 12.04 won't be a long term release.  So I installed ubuntu-desktop and uninstalled lxde desktop.

Will this now be part of the long term release?  I don't get how a specific software package (in this case lubuntu) changes the release from long term to not.

---

### Post by blackbird34 on 2012-11-13
If i understand Ubuntu in any way their 5 year support covers all the packages included in /made for the default desktop, so however you obtain ubuntu-desktop updates will come in for all its packages as long as they're available...

---

### Post by Frogs Hair on 2012-11-13
Check your version with the following command. ```
lsb_release -a
```

---

### Post by juniper1982 on 2012-11-15
hmm.  blackbird thinks i am safe.

lsb_release -a says

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

---

### Post by cwsnyder on 2012-11-15
What won't be supported beyond 18 months is the Lubuntu specific packaging (lubuntu-desktop, PCManFM, etc.)  You may have to transition to Xubuntu-desktop or Unity if you want to stay with 12.04 after October 2013 (or for many of the same packages, go with Debian 7 with LXDE).

---

