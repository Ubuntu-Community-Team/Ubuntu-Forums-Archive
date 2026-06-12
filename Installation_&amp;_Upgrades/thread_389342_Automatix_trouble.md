---
title: "Automatix trouble"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Andruk Tatum on 2007-03-20
hello, i am trying to upgrade to feisty (yes, i know the risks).  i am using the update manager like so "gksudo update-manager -c -d" and it downloads the helper, but the helper fails at downloading 122 files out of 124.  the files that it cant find are located at [www.getautomatix.com](www.getautomatix.com), which is temporarily unavailable (3/20/07 14:48:28 MST).  The upgrade just stops.  Any suggestions?  Thanks in advance.

---

### Post by taurus on 2007-03-20
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the line for automatix to comment it out.  Now, see if you can upgrade your machine.

---

### Post by Andruk Tatum on 2007-03-20
Working now, thanks!

---

