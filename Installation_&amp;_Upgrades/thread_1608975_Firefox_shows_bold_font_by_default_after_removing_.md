---
title: "Firefox shows bold font by default after removing packages"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by kc600 on 2010-10-29
I updated and removed some packages that could not be upgraded, and now Firefox and Google Chrome show web pages in bold font by default. By this i mean that all pages not setting font-weight explicitly.

Here's what i did:
```
# these would not be upgraded, so removing them
sudo aptitude remove kdebase-runtime kdebase-runtime-data plasma-scriptengine-javascript
# accepted solution that broke kdelibs5-plugins dependency, removes all kinds of kde-related packages
sudo aptitude safe-upgrade
# remove broken package, also removes more kde-related packages
sudo aptitude remove kdelibs5-plugins
sudo aptitude safe-upgrade
# no more packages not upgraded or broken
dpkg -l > ~/temp/installed.txt
# saw that font is bold by default in firefox pages, tried reinstall
sudo aptitude reinstall firefox
# no luck
```

This is on Meerkat, upgraded from long before (Lucid, i believe). I'm guessing the KDE packages are due to me having Amarok and konsole installed some time long ago, so i assumed i could ditch these.

The terminal output from the commands above is attached.

I'd appreciate any pointers.

---

### Post by kc600 on 2010-10-29
```
$ sudo dpkg-reconfigure fontconfig
```
didn't help

---

### Post by kc600 on 2010-10-29
```
$ sudo aptitude install msttcorefonts
``` fixed it.

---

