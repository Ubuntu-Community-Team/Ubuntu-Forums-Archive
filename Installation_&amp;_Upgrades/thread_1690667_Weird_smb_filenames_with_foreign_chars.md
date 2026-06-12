---
title: "Weird smb filenames with foreign chars"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by HereSomeHow on 2011-02-18
I hope this is the right forum to ask. I've recently installed an Ubuntu PC (10.04) and upgraded it to mythbuntu (i like gnome better, but needed the mythtv back/frontend). It's also the file server for my department with samba.

Basically all the clients are pc's with XP, and a few have windows 7. After I loaded the files to this "server", I allowed it to update and after that, some windows pc's started to see all the accented characters in filenames converted to underscores, stopping some batch processes that depended on paths and filenames. I applied a pair of lines to smb.conf:

```
dos charset = 850
unix charset = ISO8859-15
```

That seemed to solve the issue (altought it forced a manual renaming of all the files with accented chars), except for one machine that has windows 7 and keeps showing the filenames with an underscore instead of áéíóúñ.

Any hints of what can be wrong? Thx

---

