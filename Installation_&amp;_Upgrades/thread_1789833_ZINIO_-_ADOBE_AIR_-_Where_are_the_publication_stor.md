---
title: "ZINIO - ADOBE AIR - Where are the publication stored?"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by kamelie1706 on 2011-06-24
Hello,

I am using zinio service.
[http://www.zinio.com](http://www.zinio.com)

The reader is installed in /opt/Zinio Reader 4

What is the directory where the publications are stored?

In windows world they are in "My Documents > My Zinio Library".

Thanks,
Cyril

---

### Post by dino99 on 2011-06-24
use nautilus "search" field

---

### Post by kamelie1706 on 2011-06-24
Tried but found only 2 directories:
Zinio Reader 4
Zinio Alert Messenger

Search was done on "File system" :confused:

---

### Post by dino99 on 2011-06-24
> **kamelie1706 said:**
> Tried but found only 2 directories:
Zinio Reader 4
Zinio Alert Messenger

Search was done on "File system" :confused:

if you are looking about data/download you need to searh inside /home, not system

---

### Post by kamelie1706 on 2011-06-24
home is under "file system".

The issue was that it was under ~/.appdata and the file explorer does not search within hidden directory. How can I display hidden directory in Nautilus?

Thanks!

---

### Post by kamelie1706 on 2011-06-24
"CRTL+H" found it  :D

Anyway very strange way zinio is storing publication in Linux, they are not zno files. There is one directory per publication and one swf per page.

Does it make any sense to backup those?

---

