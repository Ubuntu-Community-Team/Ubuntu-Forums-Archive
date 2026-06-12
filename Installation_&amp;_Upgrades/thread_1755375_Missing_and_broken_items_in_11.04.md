---
title: "Missing and broken items in 11.04"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by avdheiden on 2011-05-11
Hi All,

I recently upgraded a few systems from 10.10 to 11.04. After having them up and running, I have a few issues to share.

- Some systems updated fine, but some did not. One problem that occured twice with recently installed 10.10 systems was that Unity failed to start and Gnome was broken (missing program libraries) after upgrading to 11.04
Reinstalling them from CD would fix all issues.

- The Groupwise plugin for evolution seems to be broken. Can't get it to work. Not even if I export an account from a working 10.10 system and import it on a freshly installed 11.04 system.

- In order to find out what was wrong with evolution, I tried to view the /var/log/messages. Where has that file gone ? It's only like the most important file for troubleshooting. And it's missing on every system I installed. Other people have told me they miss this file as well.
Obviously the information is stored elsewhere but I'm in the dark here.

I crashed evolution on one system. After this event, the indicator was missing in both Unity and Gnome 2. Can't seem to repair this so I had to put a shortcut on the panel instead.

---

### Post by zvacet on 2011-05-11
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo apt-get -f install
```

---

### Post by avdheiden on 2011-05-11
Thank you for your reply but I tried that of course. I also removed all of evolution and reinstalled it again and did the default repair actions for gnome panel indicators.

Did reinstall evolution-indicator etc but nothing. Once gone, the indicator never seems to return and I can't find any reason without proper logs.

Anyone know where to look for the info that would have been in /var/log/messages or how to turn /var/log/messages on again ?

---

### Post by avdheiden on 2011-05-17
Nobody ? I've spoken to several Ubuntu users I know and some of them were, just like me, missing the /var/log/messages file. So it must be a common problem.

Does anyone know of this issue and how to fix it ?

---

