---
title: "Adept Installer - Database Locked!"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by I-Am-The-Tux on 2007-06-18
I keep getting the error when I try opening Add/Remove Programs:

'Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.'

The thing is that I can't find any program that is obviously any of those applications. I've used KDE System Guard and still can't find anything. I've restarted and logged out and I still get the same message! Is there any way to kill all adept apps in either the terminal or KDE system guard. If there and I should know it, I'm sorry. I apologise, I am am a Linux noob.

---

### Post by I-Am-The-Tux on 2007-06-18
Nevermind - just found someone in another forum with the same problems and recommended I use:

sudo dpkg --configure -a

It worked.

---

