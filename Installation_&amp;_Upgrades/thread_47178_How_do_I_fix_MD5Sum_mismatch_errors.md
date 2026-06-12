---
title: "How do I fix MD5Sum mismatch errors?"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by MikeyXX on 2005-07-07
I'm getting this when I attempt to get a K console etc to install KDE. What does it mean? And how can I do this?



W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_i386.deb)
  MD5Sum mismatch

---

### Post by MikeyXX on 2005-07-07
I tried right clicking that link and downloading the file. Now I have the .deb file, what can I do with it?

---

### Post by mingus on 2005-07-07
[QUOTE=MikeyXX]I tried right clicking that link and downloading the file. Now I have the .deb file, what can I do with it?[/QUOTE]

$sudo dpkg -i <package name>

---

