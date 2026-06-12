---
title: "[SOLVED] Update Install Error"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2008-10-30
i ran sudo apt-get dist-upgrade
when i enter password for desktop it stats to run and i receive the following error

E:dpkg was interrupted,you must manually run 'dpkg--configure-a' to correct the problem

how do i do this? please help so i can update
ty
hat

---

### Post by Dumdideldum on 2008-10-30
Open a terminal or use tty2 holding CTRl+ALT+F2 (you have to provide user/pass) and type in:
sudo dpkg --configure -a

---

### Post by hatmancan on 2008-10-30
thank you ever so much Dumdideldum
workeks great.
hat

---

### Post by hatmancan on 2008-10-30
thank you ever so much Dumdideldum
workeks great.
hat

---

