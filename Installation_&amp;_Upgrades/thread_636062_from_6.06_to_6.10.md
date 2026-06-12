---
title: "from 6.06 to 6.10"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by giggolo on 2007-12-09
I have been attempting to upgrade to 6.10 from 6.06 and get the following error: failed to fetch [HTTP://people.unbuntu.com/~seb128/deb/./Packages.gz](HTTP://people.unbuntu.com/~seb128/deb/./Packages.gz) 404 Not Found.

Eventually my goal is to upgrade 7.10, any hints or sugestions.

many thanks

---

### Post by taurus on 2007-12-09
You need to edit /etc/apt/sources.list and comment out all those 3rd party repos by placing a # in front of them.  Then, try to upgrade it now.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by giggolo on 2007-12-09
I added a clean repository list from scratch and still get the following error; Failed to fetch [http://people.ubuntu.com/~seb128/deb/./Packages.gz](http://people.ubuntu.com/~seb128/deb/./Packages.gz) 404 Not Found.  Not too sure why, the repository list should not need to be edited, I got the "clean" list from here.

---

### Post by taurus on 2007-12-09
That is not the official repo so you need to comment it out if you want to upgrade your Ubuntu.  Doesn't matter if it's a clean list or super clean list.

---

