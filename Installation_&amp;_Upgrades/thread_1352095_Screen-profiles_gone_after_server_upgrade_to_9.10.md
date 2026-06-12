---
title: "Screen-profiles gone after server upgrade to 9.10"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by DigiAngel on 2009-12-11
Hello all.

So here's what I got...no screen profiles ;)  Even tried apt-get removing and reinstalling...got nothing.  The details:

lrwxrwxrwx 1 me me 47 2009-10-02 10:21 .screen-profiles/profile -> /usr/share/screen-profiles/profiles/ubuntu-dark

ls -l /usr/share/screen-profiles/profiles/ubuntu-dark
ls: cannot access /usr/share/screen-profiles/profiles/ubuntu-dark: No such file or directory

ii  byobu                                     2.38-0ubuntu3                           a set of useful profiles and a profile-switc
ii  screen-profiles                           2.38-0ubuntu3                           package renamed -> byobu
ii  screen-profiles-extras                    2.38-0ubuntu3                           package renamed -> byobu

What happened to the ubuntu screen profiles?

---

