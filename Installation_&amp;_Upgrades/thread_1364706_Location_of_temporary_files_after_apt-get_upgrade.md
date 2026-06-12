---
title: "Location of temporary files after apt-get upgrade"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by rado3105 on 2009-12-26
I tryed to upgrade system in my MID device, but there is not enough space there, and also I heard that it is not recommended. Command apt-get upgrade didnt finished, and my memory is full. I want to ask where is location of temporary files. Thanks.

---

### Post by mac9416 on 2009-12-26
Howdy,

Files downloaded by apt-get are temporarily stored in /var/cache/apt/archives. You can clean it out by running
```
$ sudo apt-get clean
```

Hope that helps!

---

### Post by rado3105 on 2009-12-26
didnt helped, it is somewhere in /usr/share, because there it is full, and disk on that MID is partitioned to to be the folder /usr/share separate partition.

---

### Post by gsmanners on 2009-12-26
If you need space in /usr/share then your only choice is to uninstall things you might not need like games, fonts, icons, mouse pointers, etc.

---

