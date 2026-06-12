---
title: "Error uppgrading to new ubuntu"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Arthur Penthaligon on 2008-01-20
I got this error while upgrading my ubuntu with the upgrading handler.
What do I do?


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz) 302 Found

---

### Post by Pumalite on 2008-01-20
Before upgrading, you have to remove all third parties from your sources.list

---

### Post by Arthur Penthaligon on 2008-01-20
How do i do that?

---

### Post by Pumalite on 2008-01-20
First backup
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
gksudo gedit /etc/apt/sources.list
Comment out (put a # in front of) all third parties, including automatix if you have it.
Save, exit, reboot, try again.

---

### Post by staticvoid on 2008-01-20
how long have you had the older version? its healthy to reinstall your OS once every 2 years. Plus its a whole new learning expirience! if your that kinda person...  :P

sv

p.s. 8.04 comes out in April btw

---

### Post by ajgreeny on 2008-01-20
Actually the references to medibuntu may well be in /etc/apt/sources.list.d/medibuntu.list not in sources.list itself.  Otherwise Pumalite's advice is spot on.

---

### Post by zipperback on 2008-01-20
It is far less problematic to simply backup your critical data, do a fresh clean install of the new version, and then just copy your critical data files back.

- zipperback
:popcorn:

---

### Post by ajgreeny on 2008-01-20
I also agree with zipperback.  Do a clean install; so much easier and gives a good clean start.

---

### Post by Pumalite on 2008-01-20
+1

---

### Post by Arthur Penthaligon on 2008-01-20
Thanks Pumalite, i have upgraded now :D

---

### Post by Pumalite on 2008-01-20
You are welcome. Good luck.

---

