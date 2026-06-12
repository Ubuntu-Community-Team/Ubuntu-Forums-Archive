---
title: "Error with apt-get update"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by mr tim esquire on 2007-04-10
Im just trying to install a new program.  I added a couple of new reposortries to etc/apt/sources.list 
and then tried 
tim@desk:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

and now i dont know what to do
please help tim

---

### Post by bulldog on 2007-04-10
Try sudo apt-get update or ```
sudo aptitude update && sudo aptitude upgrade
```

---

