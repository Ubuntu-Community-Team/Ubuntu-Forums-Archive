---
title: "Feisty upgrade error message"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by trents on 2007-04-20
Every time I try to upgrade from Edgy to Feisty with the upgrade tool, I get this message:


Failed to fetch [http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz](http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz) 302 Moved Temporarily


What do I do? 

Thanks, Steve

---

### Post by jdong on 2007-04-21
Please remove the [http://ubuntusoftware.info/](http://ubuntusoftware.info/) repository from your sources.list, then re-attempt the upgrade.

---

### Post by trents on 2007-04-21
Where is sources.list found? Is there a good utility in Ubuntu that is really helpul in searching for files? I mean one like in Windows where you can search the whole C: drive. The file searcher in Ubuntu seems to look in all the file systems but its own.

Steve

---

### Post by jdong on 2007-04-21
It is in /etc/apt/sources.list. Open up a terminal and type in

```

gksu gedit /etc/apt/sources.list

```

To edit this file.


As far as search, if you tell the search tool to Look In: Filesystem rather than <username>, it will search the entire system.

---

