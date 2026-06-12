---
title: "after hardy upgrade can't add updates or new programs"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by tiana on 2008-05-04
If I try to add a program using add/remove programs it sort of freezes.  It lets me minimize and maximize the window but it won't let me close it and I have to restart the computer if I want the non-working window to go away.

Also there are two updates that I have been trying to implement but once I hit the button to download them it does the same thing as with the program.  It freezes and I can't download anything.

---

### Post by tamoneya on 2008-05-04
try doing it through command line.
Update:```
sudo apt-get update
sudo apt-get upgrade
```

Install:
```
sudo apt-get install <package name>
```

---

### Post by tiana on 2008-05-04
It tells me "unable to resolve host laptop"

---

### Post by plucky on 2008-05-04
Can you post the output of ```
cat /etc/hosts
``` and ```
uname -a
```

---

