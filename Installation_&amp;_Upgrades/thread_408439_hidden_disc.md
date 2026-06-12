---
title: "hidden disc"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by fedorik on 2007-04-13
Hello, on my machine there was only Win XP, then i installed ubuntu as second system on same HDD. Ubuntu came with grub so i have a choice to choose what system to start at boot. Now I need to reinstall Win XP, and here is the problem. The installator can't find my disc. Does grub hide it? Can anybody help me?

---

### Post by kidders on 2007-04-13
Hi there,

Grub doesn't do anything weird with your disks. Like most bootloaders, it typically installs a small fragment of code into your MBR ... so the simple answer to your question is "No". (That's hardly very helpful though :-( )

The main problem normally encountered by users of multiple OSs is that installers like to overwrite MBRs to ensure they can boot the way *they* like to (which can temporarily prevent boot-time access to Linux).

Since it's most likely a Windows issue, your particular query may be better off on a Microsoft support forum. If you post in both places, you're *bound* to get a good answer reasonably quickly.

---

