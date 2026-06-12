---
title: "Synaptic does not yield results"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2010-03-17
Well...it cant. Cause there are no packages to search for! It says (in the lower status bar) that only 12xx packages are available...actually there are 25000+. I've selected the non free repositories.

Also, how did I update... I'm maintaining Ubuntu and I have the package index stored in some place in the hard drive (which actually resides in /var/lib/apt/lists) with the corresponding deb packages of the software that I would install using apt (before doing so, I place these deb packages in /var/cache/apt/archives) on any system.

Now, magically, for some reason, this problem stated to appear in my latest installs. That update-apt-...command does not help, I even tried deleting the index which was stored somewhere in /var/lib/apt-xb....that update-apt-...command did regenerate the index but there were no improvements. Even apt-cache search doesn't show any results.

And yes, I did apt-cache gencaches...that's standard procedure.

---

### Post by dE_logics on 2010-03-17
Ok problem got solved.

First you have to place the updated package index in /var/cache/apt/lists, then apt-cache gencaches...and THEN enable the extra repos in the software sources.

If you ever face such a problem just remove the 2 repositories temporarily, then apt-cache gencaches, then reenable the 2 repos.

However updating the package index solves all such problems.

This is a bug.

---

### Post by dE_logics on 2010-04-06
You know, Debian sucks at times.

---

