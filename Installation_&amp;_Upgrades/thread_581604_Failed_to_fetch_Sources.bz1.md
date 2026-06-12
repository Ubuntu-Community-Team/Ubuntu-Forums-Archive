---
title: "Failed to fetch Sources.bz1"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by DeathRay2K on 2007-10-19
I'm trying to upgrade from Feisty Fawn to Gutsy Gibbon through the Update Manager, but several minutes into the process I get these errors, after which it can't continue and exits:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)

What can I do about this?

---

### Post by bmorency on 2007-10-19
what happens if you try a different mirror?

---

### Post by davidjmayo on 2007-10-19
> **bmorency said:**
> what happens if you try a different mirror?

should do it there are 3 or 4 threads on different subforums having problems with Canada repos (not the first time either as they are known to be temperamental

---

### Post by ekred on 2007-10-19
I can confirm that the problem is really coming from the CA repo. Seems more like a broken server than an overloaded server!

For Ubuntu users, simply ```
sudo gedit /etc/apt/sources.list
``` or if you are using Kubuntu ```
sudo kwrite /etc/apt/sources.list
``` and replace any occurrences of "**ca.archive.ubuntu.com**" with "[COLOR="DarkOrange"]**us.archive.ubuntu.com**[/COLOR]"... or any other mirror that you know of. Now close and save the file and restart the upgrade process.

Confirmed as working for me with the **US** mirror. A lot slower than CA but at least its working! Just go watch a movie (...or 2) and take a nap and you should be fine 8)

Should actually work with any other mirrors as (like *davidjmayo* pointed out) the canadian repo is really the black sheep :???:

---

