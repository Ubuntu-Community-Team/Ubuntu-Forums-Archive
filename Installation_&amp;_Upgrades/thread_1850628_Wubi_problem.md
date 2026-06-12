---
title: "Wubi problem"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by weblearner115 on 2011-09-26
Hello everyone,

I'm trying to install Ubuntu using Wubi on my grandmother's computer so she can try it, and it has worked just fine on other computers I've tried, but every time Wubi gets close or finishes the installation, it gives me an error saying 'Permission denied', and tells me to look at a log that doesn't exist.  Can anybody help?  Thanks!

weblearner115

---

### Post by bcbc on 2011-09-26
Click on Start, Run (if XP) and enter:
%temp%\wubi-11.04-rev211.log

That will open the log file (assuming you're installing the latest version). The temp directory is hidden for some reason, but %temp% gets you there directly.

---

