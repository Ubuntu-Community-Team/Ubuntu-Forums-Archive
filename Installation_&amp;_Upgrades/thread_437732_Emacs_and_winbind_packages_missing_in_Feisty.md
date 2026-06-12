---
title: "Emacs and winbind packages missing in Feisty"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Charles Hand on 2007-05-09
After installing Feisty, apt-get and Synaptic can't find emacs or winbind, both of which I need and were available under Dapper and Edgy.

I have main, universe, restricted and multiverse repositories enabled

---

### Post by Charles Hand on 2007-05-09
I followed Taurus advise from this thread: [http://ubuntuforums.org/showthread.php?t=436637](http://ubuntuforums.org/showthread.php?t=436637)

Edit /etc/apt/sources.list and remove all "us." from all urls, then sudo apt-get update. All is well now.

---

