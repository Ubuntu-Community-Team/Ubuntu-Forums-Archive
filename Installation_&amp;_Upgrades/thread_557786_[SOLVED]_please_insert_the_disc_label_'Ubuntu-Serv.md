---
title: "[SOLVED] please insert the disc label 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i38"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by apollon1234 on 2007-09-23
Hi, I've been trying to install different software on my server and i've met some problem while trying to install software like SSH or VSFTP.

Everytime I try to install those programs, i get this message :

> Media change: please insert the disc labeled
 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

Event when I have the CD in my CDROM drive, this message keep spamming, so I can't get the installation done...

Is there any way to bypass, or fix that? 

Thank you very much for your time.

---

### Post by Herman on 2007-09-23
```
sudo gedit /etc/apt/sources.list
```The top portion of the file before editing it,```
# 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

```The top portion of the file after it has been edited,```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

```Hello apollon1234,
Edit your sources.list file and 'hash out' the lines referring to the CD-ROM. Save the changes and close the file. That should fix it. 
Regards, Herman :)

---

### Post by apollon1234 on 2007-09-23
Thank you very much it work now :)

---

