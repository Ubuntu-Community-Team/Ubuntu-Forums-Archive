---
title: "invalid signature"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by headlessspider on 2008-04-30
while manually running the update manager i got this error

[INDENT]W: GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/INDENT]
no hangs or anything. i just thought that somebody at ubuntu may not be aware of the error.

---

### Post by zvacet on 2008-04-30
Refresh your source list with 

```
sudo apt-get update
```

---

