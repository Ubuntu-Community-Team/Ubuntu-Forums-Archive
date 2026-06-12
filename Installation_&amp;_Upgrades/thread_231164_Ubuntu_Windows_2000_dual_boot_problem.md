---
title: "Ubuntu Windows 2000 dual boot problem"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by dphipps on 2006-08-07
I recently installed Ubuntu on my parents computer.  I left Windows 2000 an the first partion and installed Ubutnu on the second.  The problem is that now I can not boot up Windows.  I had to add the fallowing lines to menu.1st manually.
```
title		Windows 2000
root		(hd0,0)
makeactive
chainloader	+1
```

When I try to boot Windows this it I get an error saying that the file system is unknown.  Is there anyway, other that reinstalling, for me to fix this.

---

### Post by dphipps on 2006-08-08
I reinstalled Windows and now I have it set up so that I can boot both Linux and Windows from Grub.  The problem is that every time Windows is booted it changes the boot flag to the first partion.  I then have to use a live cd to change it back.

Does anybody know that I can do about this.

---

