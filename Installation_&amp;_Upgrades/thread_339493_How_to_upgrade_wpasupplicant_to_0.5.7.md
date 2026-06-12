---
title: "How to upgrade wpasupplicant to 0.5.7?"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by rockwill on 2007-01-15
I got a wired error when the system was trying to upgrade wpasupplicant from 0.5.5 to 0.5.7. Now I can't event remove the old version. I had removed kwlan and all other wifi related apps, but still this wpa can't be removed. Here is the error message when I typed sudo apt-get autoremove:

Selecting previously deselected package wpasupplicant.
(Reading database ... 193668 files and directories currently installed.)
Preparing to replace wpasupplicant 0.5.5-3v1ubuntu4 (using .../wpasupplicant_0.5.7+3v1ubuntu3_i386.deb) ...
Unpacking replacement wpasupplicant ...
dpkg: warning - old post-removal script returned error exit status 10
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 10
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone has an idea what should I do?

---

### Post by smolko on 2007-01-16
I've just posted a solution[http://www.ubuntuforums.org/showthread.php?p=2020462#post2020462]("http://www.ubuntuforums.org/showthread.php?p=2020462#post2020462"), that worked for me.

---

### Post by rockwill on 2007-01-16
Hey, thanks.
Simple and works.

---

### Post by dfourth on 2007-01-17
ditto thanks for a quick solution to an annoying problem

---

