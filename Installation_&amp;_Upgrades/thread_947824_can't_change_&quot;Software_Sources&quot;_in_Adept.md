---
title: "can't change &quot;Software Sources&quot; in Adept Installer"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by d.marcu on 2008-10-14
I upgraded from kde 3.5.9 to kde 3.5.10. In order to do that i checked "unsupported updates" (advice from here -->  [http://dot.kde.org/1219751598/1219780288/1219783458/1219784312/1219785876/1219786011/SoftwareSources.jpeg](http://dot.kde.org/1219751598/1219780288/1219783458/1219784312/1219785876/1219786011/SoftwareSources.jpeg)). 
My problem is that now the "Edit Software Sources" button is inactive, so if i can't change any settings. Adept installer asks for my root password every time it starts so it's not a problem of administrative rights.
thanks

---

### Post by dabl on 2008-10-14
You can edit (in root mode) the file /etc/apt/sources.list and put a "#" in front of the line that you want to disable.  It should be kinda obvious which one it is, when you're looking at the open file and the source lines.  :)

---

