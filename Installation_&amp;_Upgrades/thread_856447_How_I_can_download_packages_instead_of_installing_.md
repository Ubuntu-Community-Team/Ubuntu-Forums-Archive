---
title: "How I can download packages instead of installing them"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by pedramslhr on 2008-07-11
hi
I'm using Ubuntu 8.04
do you know how i can download packages to install them from my computer and for archive purposes?
tanx!

---

### Post by avtolle on 2008-07-11
From memory: open Synaptic; click on Packages, then Preferences; IIRC, there is a radio button to select the text to which says something akin to leave in cache only. Click that, hit apply, and exit Synaptic.

---

### Post by toolzen on 2008-07-11
or from the cli: 

# apt-get -d package-name

---

### Post by pedramslhr on 2008-07-11
> From memory: open Synaptic; click on Packages, then Preferences; IIRC, there is a radio button to select the text to which says something akin to leave in cache only. Click that, hit apply, and exit Synaptic.
I found the radio button
and installed a package,
now a ".deb" file should be found in cache folder or its subfolders. yes?
tanx

---

### Post by avtolle on 2008-07-11
It stays, as I recall, in the cache. There's another thread on the Forum today about moving the file to another system, look around and you will (hopefully) find it.

---

### Post by pedramslhr on 2008-07-11
> or from the cli:

# apt-get -d package-name

so where the downloaded file will be stored?
and how i can know the package name that should be used.(from synaptic?)
can you please show with an example?
tanx

---

### Post by avtolle on 2008-07-11
Read this thread through: [http://ubuntuforums.org/showthread.php?t=856380](http://ubuntuforums.org/showthread.php?t=856380) I think it answers your questions.

---

