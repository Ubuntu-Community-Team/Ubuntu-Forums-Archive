---
title: "Stop graphical login"
date: 2005-02-14
forum: Installation &amp; Upgrades
---

### Post by iigs on 2005-02-14
How do I stopt he graphical login on Ubuntu?  I looked in /etc/inittab but runlevel is already set to 2.

thanks,

iigs.

---

### Post by Buffalo Soldier on 2005-02-14
Go to

Computer -> System Configuration -> Login Screen Setup

---

### Post by dejot on 2005-02-14
sudo update-rc.d -f remove gdm

works fine.

---

### Post by iigs on 2005-02-14
Thanks to both of you,  cli login only here now :D

---

