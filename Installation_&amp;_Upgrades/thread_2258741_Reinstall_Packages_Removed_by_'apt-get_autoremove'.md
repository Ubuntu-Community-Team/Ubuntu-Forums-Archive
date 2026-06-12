---
title: "Reinstall Packages Removed by 'apt-get autoremove'"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by VSFDELHI on 2014-12-30
After upgrading the installation using apt-get upgrade, I ran the command apt-get autoremove. After the command was run, I realised that the gnome environment looked differed considerably, especially in the themes. Is there any way I can reinstall the packages removed by autoremove command or fetch a list of those packets that have been removed?

---

### Post by schragge on 2014-12-30
APT keeps its log in file /var/log/apt/history.log All recently installed/upgraded/(auto)removed packages should be listed there.

---

