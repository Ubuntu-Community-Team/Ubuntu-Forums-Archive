---
title: "Upgrade from Gutsy to Hardy Problems"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by MattyGabe on 2008-04-27
My current Gutsy installation cannot upgrade to 8.04.

I tried doing it through the graphical upgrade manager.  It has the 8.04LTS Upgrade button.  I press it, it goes to download it, and says that it cannot unpack the archive.

I try sudo apt-get upgrade.  It lists two 7.04 files, but does nothing.

I try do-release-upgrade, and it goes to get it, and tells me:
Failed Upgrade tool signature
Failed Upgrade tool

And then it cant unpack the archive.

A bit frustrated right now, so any help would be greatly appreciated.

---

### Post by Pumalite on 2008-04-27
System>Administration>Software Sources>Downlo0ad From>Other>Let it choose the best for you.
Try again.
Don't forget:
sudo apt-get update
sudo apt-get upgrade 
first.

---

### Post by MattyGabe on 2008-04-28
> **Pumalite said:**
> System>Administration>Software Sources>Downlo0ad From>Other>Let it choose the best for you.
Try again.
Don't forget:
sudo apt-get update
sudo apt-get upgrade 
first.

Thanks for the suggestion, but no dough.

I went through, let it run the ping tests to choose the best server, it chose the best server.  I then try to save the settings, it attempts to re-load the software information, and then it cannot access the repositories.

---

### Post by bilal.17 on 2008-04-28
try disabling third party software in system sources

---

### Post by Pumalite on 2008-04-29
Good idea. Make sure your connection is OK. too.

---

