---
title: "Restrictions after Update"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2007-04-26
Is this restriction important?
----------------------------------------------

cat /etc/apt/sources.list

#AUTOMATIX REPOS START
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

#AUTOMATIX REPOS END

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted #Added by software-properties
roger@roger-desktop:~$

---

### Post by STREETURCHINE on 2007-04-26
they look normal,what is your major concern?


except what version are you using dapper or feisty

---

### Post by Vorian on 2007-04-26
maybe you can get some better answeres at [www.getautomatix.com](www.getautomatix.com)

also, see [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

