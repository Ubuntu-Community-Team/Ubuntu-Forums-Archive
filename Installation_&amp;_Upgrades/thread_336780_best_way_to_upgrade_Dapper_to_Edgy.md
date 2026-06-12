---
title: "best way to upgrade Dapper to Edgy?"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by Pollywoggy on 2007-01-12
I have just installed Kubuntu and when I run 'update-manager -d' as root, it does upgrade packages but when I try to upgrade to Edgy it fails with "can't find DistUpgradeViewGtk"

I suppose the best way to upgrade (to do a dist-upgrade) is with apt.
Would I just change /etc/apt/sources.list by replacing all mentions of "dapper" with "edgy" or is it more complicated than that?  I have used Debian for about 8 yrs and also Linspire and Freespire, but I am new to Ubuntu.

thanks

---

### Post by mkoyle on 2007-01-22
It appears that you can upgrade that way (if you haven't already done it).  The only problem that may arise is if you have unofficial / unusual repositories.

The recommended upgrade for xubuntu appears to be downloading the CD image and using apt-cd.  Look at [http://www.ubuntuforums.org/showthread.php?t=285951](http://www.ubuntuforums.org/showthread.php?t=285951)

--Matthew

---

