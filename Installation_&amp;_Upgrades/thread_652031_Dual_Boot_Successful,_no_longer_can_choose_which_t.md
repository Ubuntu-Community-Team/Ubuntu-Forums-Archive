---
title: "Dual Boot Successful, no longer can choose which to boot from."
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by PaddyTheChump on 2007-12-28
Hi, Last night I successfully dual booted windows xp and 7.10
However, when I tried to boot xp, it said there were some missing files, so I couldn't boot.
I reinstalled xp on the same partition I had before, but now I can no longer choose to boot from ubuntu 7.10 or xp.
Does anyone know how to fix this?
Thanks

---

### Post by taurus on 2007-12-28
You need to reinstall GRUB to MBR again since XP overwrote it when you reinstalled it again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by jken146 on 2007-12-28
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sef on 2007-12-28
XP overwrote GRUB, and MS OSes only see other MSOSes.   Download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It is easy to use.

---

### Post by PaddyTheChump on 2007-12-28
Thanks!
I'll give this a shot later, I've got to head out to the store now.
One step closer to eliminating Microsoft entirely for me.

---

