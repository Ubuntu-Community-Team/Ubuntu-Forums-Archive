---
title: "Lucid Lynx Flashplayer Install Problem"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by greenfrog on 2010-05-03
This is the error I get when using apt-get upgrade or package manager

dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

What do I do now to correct this situation?


Thanks :(:(:(

---

### Post by adam-red on 2010-05-03
It sounds like the package isn't fully installed so it wants you to install it.

sudo apt-get install flashplugin-nonfree
sudo apt-get remove flashplugin-nonfree

And see if it likes that.

---

