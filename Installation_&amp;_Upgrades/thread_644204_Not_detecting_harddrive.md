---
title: "Not detecting harddrive"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Silenus on 2007-12-18
I just tried to reinstall with a dual boot, I already have xp. I tried debian, and ubuntu both could not detect the harddrive and asked for drivers for it, it is an 120 gb serial ata drive, and I have installed to it before, so I don't know what it wrong, or what could cause this.

---

### Post by Pumalite on 2007-12-18
Get Gparted Live CD and check if it sees it. If is does, resize your XP partition (right click on partition, choose 'resize' from menu). Then install Ubuntu in that partition going Manual:
10 GB for '/'
1 or 2 GB for /swap
The rest for /home

---

