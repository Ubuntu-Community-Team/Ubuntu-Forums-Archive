---
title: "Is it possible to transfer settings to another computer?"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by Dawnshadow on 2006-08-06
Hi!

I have had Ubuntu installed on a spare computer we had for a while, and I've decided to put it on my main computer, too (provided the hardware is compatable) and dual-boot it with Windows XP (because I'm a game junkie and some of the games aren't WINE-compatable.) If I copy my user directory from this computer onto that one, will it copy my settings, downloaded themes, etcetera over, too? (I assume I'd have to install my programs again, which isn't too hard because they're  all in one place....) Or should I just go ahead and hunt everything down again and set it up manually?

Thank you.

--Dawn

---

### Post by malacandra on 2006-08-06
I think you can do this by making a separate partition on your computer for your home directory (and separate / partition) and then copying the home directory on your spare comp to the new one. You could probably do it all on one partition, but it's better to have a separate partition for your personal data and settings, in case you ever reinstall or install a different distro.

---

### Post by aysiu on 2006-08-06
The copy command isn't so simple as just *cp*.

Look here for more details: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

To be safe, I'd just copy over your email and browser settings.

---

