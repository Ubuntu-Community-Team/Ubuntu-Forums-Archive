---
title: "Beagle install problem"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by gabng on 2006-06-13
I'm trying to install Beagle by following the instructions from here [http://beaglewiki.org/Installing_Beagle](http://beaglewiki.org/Installing_Beagle)

I couldn't find the package mono-data-sqlite in synaptics and when I tried to apt-get it, it said it couldn't find the package.  As for the other packages listed, I installed them all.

I moved on to ./configure and it failed with
```
checking for mono.pc... configure: error: missing the mono.pc file, usually found in the mono-devel package
```

I searched and couldn't find the mono.pc file anywhere, but I'm sure the mono-devel package is installed.

Does anyone know where I can find this file?  Or is there another way to install Beagle?  I searched the forums and couldn't find posts related to Beagle install.  Can someone please help me out?

---

### Post by johnc4510 on 2006-06-13
System>Administration>Synaptic Package Manager
Mark beagle for install and apply.

---

### Post by gabng on 2006-06-13
Thanks!  I have beagle running now, but I'm getting these messages
```
inotify_add_watch: Permission denied
```
in the terminal.
What is going wrong?
Also, how do I integrate Beagle into deskbar?  Since I couldn't see it listed in its preference.

---

