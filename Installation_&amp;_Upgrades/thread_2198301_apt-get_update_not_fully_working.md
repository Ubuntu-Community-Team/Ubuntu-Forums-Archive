---
title: "apt-get update not fully working"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by roberto32 on 2014-01-08
I run apt-get update it install soem updates but, when I run software updater right after that it sitll has some updates? or the SWupdater pops up at the bottom pannel - there are some new updates I cancel it then run apt-get update and then SW updater and there are new updates?? I think it's osme kind of bug

---

### Post by Alculete on 2014-01-08
try ```
sudo apt-get install -f
``` maybe you have some packages with conflicts and then again try ```
sudo apt-get update again
```

---

### Post by Bucky Ball on 2014-01-08
Open a terminal and these commands, one after the other:

```
sudo apt-get update
sudo apt-get upgrade
```

Post any error messages. If you do get an error message it may suggest running the command given by Alculete:

```
sudo apt-get install -f
```

---

### Post by efflandt on 2014-01-09
"sudo apt-get **update**" only gets a list of updates, it does not install them. That is why the SW updater still shows available updates. After that "sudo apt-get **dist-upgrade**" is smart about installing updates, including any changing dependencies. "sudo apt-get **upgrade**" is not as smart because it upgrades existing packages, but may skip some packages if dependencies change. Read "man apt-get".

---

