---
title: "How to install VLC player in Ubuntu 11.10 Oneric 32 Bit."
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by Yuva Raj on 2012-08-11
Hi,

I Downloaded .deb(debian Package) & opened with gdebi.
It popped out,it was a wrong architecture amd 64.

By using,PPA Method..i get the following Error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'vlc' has no installation candidate


Please ! Solve my Problem...I Cant able to play any media files!!

---

### Post by raja.genupula on 2012-08-11
VLC is already in repo's of Ubuntu . look at the software center with search as VLC media player .

---

### Post by shubham1 on 2012-08-11
> **Yuva Raj said:**
> Hi,

I Downloaded .deb(debian Package) & opened with gdebi.
It popped out,it was a wrong architecture amd 64.

By using,PPA Method..i get the following Error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'vlc' has no installation candidate


Please ! Solve my Problem...I Cant able to play any media files!!
run in terminal:
sudo apt-get install vlc

---

### Post by raja.genupula on 2012-08-11
> **shubham1 said:**
> run in terminal:
sudo apt-get install vlc


Thats not going to be fine . to install everything with VLC ,software center is the best way he have .

:D

---

### Post by Yuva Raj on 2012-08-11
> **raja.genupula said:**
> Thats not going to be fine . to install everything with VLC ,software center is the best way he have .

:D


I Uninstalled Software Center accidently when i was beginner. I Searched but i can't able to find for 32 bit architecture :\

---

### Post by raja.genupula on 2012-08-12
ok you can install it by doing this command from your terminal

```
sudo apt-get install software-center
```

---

