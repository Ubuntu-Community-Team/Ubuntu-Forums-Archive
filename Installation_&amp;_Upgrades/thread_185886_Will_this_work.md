---
title: "Will this work?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by echo $USER on 2006-06-01
# sed s/brezzy/drapper/g /etc/apt/sources.list
# update-manager -d

Is that all i need to do?  Thanks for the help.

---

### Post by carlosqueso on 2006-06-01
Actulally, all you need to do is 

```
gksudo "update-manager -d"
``` and it should do the rest.  DO NOT change your sources.list

---

### Post by echo $USER on 2006-06-01
What is gksudo?  How is it different from sudo?  Thanks for letting me know before I screwed up my sources.list.

---

### Post by aysiu on 2006-06-01
*gksudo* is for graphical Gnome applications.
*kdesu* is for graphical KDE applications.
*sudo* is for terminal commands.

---

### Post by echo $USER on 2006-06-01
oh, okay, thanks!

---

