---
title: "[SOLVED] Can't acces as root?"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by socngill on 2008-11-04
Help!

Need to amend my sources.list file but the right click no longer gives and option to openas root, and the options on the right of the file system no longer exist.

How can I get this back?  Besides uninstalling and installing 8.04....

---

### Post by Partyboi2 on 2008-11-04
deleted

---

### Post by taurus on 2008-11-04
You can always run it from a terminal.

```
kdesu kwrite /etc/apt/sources.list
```

---

### Post by socngill on 2008-11-04
Thanks.  Tried that but Kwrite seems to have been removed from my system during the upgrade..

Now I can't get adapt to open as I added some source lists via adapt but missed out part of the name when copying the text so now apt-get doesn't work and adapt won't open. doh!

---

### Post by iponeverything on 2008-11-04
nano maybe?

sudo nano /etc/apt/sources.list

---

### Post by socngill on 2008-11-04
You are an absolute star!!  Never come across that command before.

---

