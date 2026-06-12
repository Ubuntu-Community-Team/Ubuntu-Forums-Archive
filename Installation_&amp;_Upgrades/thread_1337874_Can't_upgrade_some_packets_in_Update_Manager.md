---
title: "Can't upgrade some packets in Update Manager"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Metalmex on 2009-11-25
(Karmic Koala) I'm having some trouble with the update manager. it works but with some packets it doesn't. When i click on the "check for updates" it says i'm up-to-date(i can install the daily updates), but it also scans 53 packets which i can't install. I post a picture

---

### Post by whoop on 2009-11-25
Maybe the ubuntu cd-rom is in your sources list.. You can get rid of that:
```

gksudo gedit /etc/apt/sources.list

```
Add a "#" without the quotes in front of the cd-rom line(s)...

---

### Post by MelDJ on 2009-11-25
or go to system-administration-software sources.  then under the ubuntu software tab, uncheck the cdrom.

this is because, as said by whoop, the cdrom has become a repo. since you took the ubuntu cd out of the cd rom, it cant find the repo hence giving you the error message

---

### Post by Metalmex on 2009-11-26
thanks guys it work perfectly. I tried the second post. Problem Solved

---

