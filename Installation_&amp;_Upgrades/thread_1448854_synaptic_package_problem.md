---
title: "synaptic package problem"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by etcall911 on 2010-04-07
i have a problem in opening my synaptic package manager:(
everytime open it will show ****:

E: Type '<?xml' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



please help:(

---

### Post by oldos2er on 2010-04-07
Open the file as administrator ```
gksu gedit /etc/apt/sources.list.d/winehq.list
``` and add a comment mark # in front of line 1, and any line that doesn't begin with deb or deb-src.

After you've done that, run ```
sudo apt-get update
``` or in Synaptic click 'Reload'.

---

