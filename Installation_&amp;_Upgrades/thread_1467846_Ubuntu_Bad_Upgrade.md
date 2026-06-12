---
title: "Ubuntu Bad Upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2010-05-01
Hello,
 
I decided to upgrade to Ubuntu 10.04 LTS from Ubuntu 9.10 earlier today. I started the upgrade process, after around 4 hours everything was starting to install. But then certain errors began to pop up. Soon after, the upgrade dialog exited because of too many errors (a screenshot is attached below with other documents). 
 
Does anyone know a fix to this? Right now I have to back up by files and do a fresh reinstall.
 
Icons are all over the place, some have been deleted, and application menus are "scrambled". Nothing really seems to work except my web broswer, Opera, which isn't a Canonical Ubuntu application.
 
I have attached to screenshot of the upgrade dialog and the other documents the error dialog wanted me to attach.
 
Anyhelp is appreciated!
 
Thank you all very much - looking forward to Ubuntu 10.04!
 
-Justin Reno

---

### Post by prshah on 2010-05-01
> **JustinR said:**
> 
Does anyone know a fix to this? Right now I have to back up by files and do a fresh reinstall.

As recommended in the dialog, give the terminal (Applications-Accessories-Terminal) command```
sudo dpkg --configure -a
``` (Or without the sudo if from recovery mode)

See [this thread on recovering a failed upgrade]("http://ubuntuforums.org/showpost.php?p=4872499&postcount=1") for more details.

---

