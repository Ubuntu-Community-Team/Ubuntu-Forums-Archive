---
title: "Using Ubuntu Desktop Disk with Ubuntu Server"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by TheJerryMan on 2007-09-10
Hello all,

Is it possible to install gnome (Ubuntu desktop) using the Ubuntu desktop CD on an Ubunutu server machine.

I know you can do this with ```
apt-get install ubuntu-desktop
``` using the internet but I’ve live in a bandwidth challenged country and need to avoid this if possible.

---

### Post by logos34 on 2007-09-10
No, I think you'd need the Alternate CD to do that.

---

### Post by TheJerryMan on 2007-09-12
From what I understand, the alternate CD is just the live CD minus the live part.

Can't I just hack the cdroms.list and the sources.list? Can anyone explain how the aptitude/apt-get package manager works, for example the installation structure?

---

### Post by pxwpxw on 2007-09-12
You could try just using 
```

 apt-cdrom add
 apt-get update

```
disconnect the network, and then try the desktop install, you may have to comment out network mirrors from the sources.list. Can't say I ever tried that though.

edit, may need sudo.

---

