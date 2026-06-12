---
title: "installation of updates"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Gavinholmes on 2008-03-29
Hi everyone, im very impressed with this software, but still having afew small teething problems. The main one is for music and playing restricted medias 'Ubuntu restricted extras' and all other updates. when i go to install this it keeps on coming up with this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Im a complete novice to this, so how do you manually install a programme ,if you repley please make it simple for me. the system i have is a Acer apsire 1353 VX and im running Xubuntu Linux 7.10 i386

Cheer Gav

---

### Post by Pumalite on 2008-03-29
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
Post the output here.

---

