---
title: "abiword problem"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by eoinmonty on 2005-11-09
Hi i am having a problem with abiword im fairly sure i never installed it yet i can not install or update anything as i keep getting this error

"The following packages have unmet dependencies:
abiword-common: Depends: abiword but it is not installed or
abiword-gnome but it is not installed
E: Unmet dependencies. Try using -f."

if i open synaptic it tells me that the abiword-common package is broken but its unable to fix it

i also am unable to uninstall abi-word common i get this error

dpkg: parse error, in file `/var/lib/dpkg/status' near line 857 package `abiword-gnome':
missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

thanks in advance!

---

### Post by Lambert on 2005-11-09
Make sure you have universe and multiverse repositories set up.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Then from a terminal type sudo apt-get update or from synaptic hit reload. Then try to install again.

Basically what's happening is there are some files abiword depends on that can't be found during install. Adding the repositories should fix this.

---

