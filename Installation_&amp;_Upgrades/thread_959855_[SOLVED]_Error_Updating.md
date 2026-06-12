---
title: "[SOLVED] Error Updating"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by MobiTec on 2008-10-26
Hi guys, i'm a complete noob when it comes to linux so bare with me..

i tried to run some updates on my linux laptop and i keep getting this error

```
dpkg: unable to install new triggers deferred file `/var/lib/dpkg/triggers/Unincorp': 
No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

```

I'm running Ubuntu 8.04 Hardy Heron

Any tips on how i can resolve this??

---

### Post by MobiTec on 2008-10-27
Solved by mixing other similar threds with similar problem...

1, Moved the file (to a backup) as i couldn't delete or edit it
```
sudo mv /var/lib/dpkg/triggers/Unincorp.new /var/backups/Unincorp.bak
```

2, Went to move it back but error occured "no such file in dir"
```
sudo mv /var/backups/Unincorp.bak /var/lib/dpkg/triggers/Unincorp
```

So i left the file there...

3, Cleaned
```
sudo apt-get clean
```

4, Updated
```
sudo apt-get update
```

Ran Update manager and all went well...

---

