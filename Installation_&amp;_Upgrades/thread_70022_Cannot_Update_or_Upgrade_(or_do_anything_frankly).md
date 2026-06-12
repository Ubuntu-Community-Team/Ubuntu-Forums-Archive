---
title: "Cannot Update or Upgrade (or do anything frankly)"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by Valencik on 2005-09-28
Pretty simple, I try sudo apt-get update, or go into Synaptic Package manager and hit Ctrl+R to download the repository indexes and I get this:

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found


Why? How do I fix it so I can update ubuntu.

Thank you in advanced.

---

### Post by Muhammad on 2005-09-28
I suggest you change the upgrade mirrors by gediting the sources.list. ;)

---

### Post by Leif on 2005-09-28
the unofficial backports repositories are being shut down : [http://ubuntuforums.org/showthread.php?t=69681](http://ubuntuforums.org/showthread.php?t=69681)

---

### Post by XDevHald on 2005-09-28
The Backports are now Official: [http://www.ubuntuforums.org/showthread.php?t=69681&highlight=Backports]("http://www.ubuntuforums.org/showthread.php?t=69681&highlight=Backports")

Please remind other users about this as it has been a task for me all day ;)

P.S Thank You Leif!

---

### Post by Valencik on 2005-09-28
Thanks that helped.

---

