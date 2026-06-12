---
title: "Apt-get and cd installation"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by kpm on 2006-09-09
I just installed the Ubuntu barebones server and then ran apt to install openssh... Rather than simply install openssh, I was prompted to put the cd in the drive to install openssh.  Is there a config file I have to edit so when software is installed with apt, there is no prompt for a CD in the drive anymore??

Thanks

---

### Post by whizbaby on 2006-09-09
Edit your */etc/apt/sources.list* (e.g. **sudo nano /*etc/apt/sources.list***) and put a # in front of lines wich contain the cd as repository.(being there you could also remove the #'s before lines which contain *universe* or *multiverse*)

---

### Post by kpm on 2006-09-09
> **whizbaby said:**
> Edit your */etc/apt/sources.list* (e.g. **sudo nano /*etc/apt/sources.list***) and put a # in front of lines wich contain the cd as repository.(being there you could also remove the #'s before lines which contain *universe* or *multiverse*)

Ahhh! Right.  Thanks.

---

