---
title: "Problems installing ubuntu 8.04"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Sukainami on 2008-06-23
I recently tried upgrading my ubuntu to version 8.04 and let it run over night. I ran it today and it works fine, all the way up until I log my user in, then all it does is show my desktop icons on a blank screen, and if I click on them it returns me to the log in menu. Luckily I have kubuntu 7.1 on my computer as well so I could get this out there, any help would be appreciated, a solution that doesn't involve losing my photos and music would be preferred.

---

### Post by ibutho on 2008-06-23
Hi. 

Have you tried running the upgrade again via the terminal i.e. at the login screen do CTRL-ALT-F1 then login to the terminal and run
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Also try creating a new user account (using adduser or useradd) and see if you can login successfully into that account. If you can, try deleting the ~/.gnome* directories (after backing them up first) of your old user account and try to login again.

---

### Post by Sukainami on 2008-06-23
> **ibutho said:**
> Hi. 

Have you tried running the upgrade again via the terminal i.e. at the login screen do CTRL-ALT-F1 then login to the terminal and run
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Also try creating a new user account (using adduser or useradd) and see if you can login successfully into that account. If you can, try deleting the ~/.gnome* directories (after backing them up first) of your old user account and try to login again.
Thanks, I'll try that.

---

