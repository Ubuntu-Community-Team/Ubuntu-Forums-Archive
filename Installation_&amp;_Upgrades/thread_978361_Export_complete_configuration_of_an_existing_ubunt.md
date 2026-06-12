---
title: "Export complete configuration of an existing ubuntu installation to a new one?"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by bakom on 2008-11-11
Hello,

is it possible to export the whole configuration (Gnome, installed packages, etc) of an existing ubuntu system and import it to a new one?

Thanks!

---

### Post by ciscosurfer on 2008-11-11
You can download aptoncd from the repositories **sudo apt-get install aptoncd**[INDENT] Description: Installation disc creator for packages downloaded via APT
 APT removable repository creator and package backup tool for Debian based
 systems.
 .
 This tool will allow you to create a media (CD or DVD) to use to install
 software via APT in a non-connected machine, as well upgrade and install
 the same set of softwares in several machines with no need to re-download
 the packages again.
 .
 For more information, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)
[/INDENT]Other personalized configuration files can simply be copied to removable media as well and placed back in their respective places upon a resintall.

Edit: There's also [this thread]("http://ubuntuforums.org/showpost.php?p=4487846&postcount=12") and [this thread]("http://ubuntuforums.org/showpost.php?p=4401444&postcount=10").
.
.
.

---

