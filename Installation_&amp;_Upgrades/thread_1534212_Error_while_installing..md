---
title: "Error while installing."
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by adeee on 2010-07-19
Guys i download wubi from [http://wubi-installer.org/](http://wubi-installer.org/) and when i install there is error. looks like this. 


[ATTACH]163906[/ATTACH]


So help me to remove it./:(

---

### Post by bcbc on 2010-07-19
You're getting a permission error. Make sure you're running as an administrator. If you're not installing from a CD make sure you have an active internet connection.

If you look in the log file referred to, it lists every wubi install/uninstall you do per release. You can search for the last permission and see what it's complaining about. (To get there, just open explorer and type %temp% in the address bar, then look for the file mentioned in popup - wubi.log or something similar).

---

