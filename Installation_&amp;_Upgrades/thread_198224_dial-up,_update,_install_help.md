---
title: "dial-up, update, install help"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by Fittersman on 2006-06-16
I have breezy and i want to update to the new one.

I do not want to install again, i want to update because i did alot of work before to get it to work sorta. I have update manager and the new ubuntu downloaded and burned on a cd. I have no access through ubuntu to the internet because my modem doesnt work. i need to know how to get the modem working and how to update my system.

---

### Post by Fittersman on 2006-06-18
anyone?

---

### Post by aysiu on 2006-06-18
I have no idea how to get modems working in Ubuntu.

But if you have the new Ubuntu Alternate Install CD (instead of the Desktop CD), you can upgrade with that CD.

Just type ```
sudo apt-cdrom add
``` and pop the CD in. Then ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

