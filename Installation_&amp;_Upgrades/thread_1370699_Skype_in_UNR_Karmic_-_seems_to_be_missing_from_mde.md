---
title: "Skype in UNR Karmic - seems to be missing from mdeibuntu!"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by harry.braviner on 2010-01-02
I'm trying to install Skype onto my netbook. I'm running Ubuntu Netbook Remix, Karmic.

Every set of instructions I've found tells me to add

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

to my sources.list, and then to install the package "skype". I've added such a line, and done "apt-get update", but no such package seems to exist.

The result of looking for it is just

harry@kepler:/etc/apt$ apt-cache search skype
skytools - Database management tools from Skype to PostgreSQL
python-skype - Skype API wrapper for Python
skysentials - extra functionalities for Linux Skype client

Apt did not report any problems during the update. Am I missing something obvious?

---

### Post by fiklein on 2010-01-03
Suggest this link:
[http://ubuntuforums.org/showthread.php?t=1293226](http://ubuntuforums.org/showthread.php?t=1293226)

---

