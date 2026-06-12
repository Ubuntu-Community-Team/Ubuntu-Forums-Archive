---
title: "ubuntu 10.04 trouble with partition"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by XaverOzz on 2010-05-07
i have a problem with install 10.04 the installers sais what there is no partition on my disk where i have 2 ext4 partition 1 swap and 1 ntfs. have someone simmilar problem?

---

### Post by dino99 on 2010-05-07
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by XaverOzz on 2010-05-07
thx but i already have formatted partitions i use ubuntu 9.10 and want to go on ubuntu 10.04 but the installer said that there is no partitions on my sda

---

### Post by gazmend on 2012-03-25
> **XaverOzz said:**
> thx but i already have formatted partitions i use ubuntu 9.10 and want to go on ubuntu 10.04 but the installer said that there is no partitions on my sda
From terminal of live sesion :

**sudo apt-get remove dmraid **


**sudo apt-get install gparted **

---

