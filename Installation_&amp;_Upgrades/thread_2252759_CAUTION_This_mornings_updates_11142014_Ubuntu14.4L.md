---
title: "CAUTION: This mornings updates 11/14/2014 Ubuntu14.4LTS"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2014-11-14
Opened Synaptic and noticed a number of gle and mesa packages to update along with xatracker and calculator.
If trying to update the entire list a notice of removal of a great number of packages which were important to my system operations would be removed.
Certain files, if installed first, change the dependency issue and allow the install of the updates without the apparent dependency removal.
 Be careful and when trying to install make sure you pick packages which do not want to remove anything fisrt.
There is probably a dependency issue with the newer packages on one of the newer installs which, if it is not installed first will cause the removal notice.

---

### Post by ajgreeny on 2014-11-14
Give us some details please; I've just updated my VBox installation of 14.04 and there were no difficulties or packages to remove or anything like that.
Have you got some ppa repos enabled that may have brought in packages which are not in the usual repos that might then cause dependency problems?

This is what my update gave me today:-
```
Upgraded the following packages:
chromium-codecs-ffmpeg-extra (37.0.2062.120-0ubuntu0.14.04.1~pkg1049) to 38.0.2125.111-0ubuntu0.14.04.1.1061
flashplugin-installer (11.2.202.411ubuntu0.14.04.1) to 11.2.202.418ubuntu0.14.04.1
gir1.2-gudev-1.0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
gnome-calculator (1:3.10.2-0ubuntu1.2) to 1:3.10.3-0ubuntu0.1.1
libcurl3 (7.35.0-1ubuntu2.1) to 7.35.0-1ubuntu2.2
libcurl3-gnutls (7.35.0-1ubuntu2.1) to 7.35.0-1ubuntu2.2
libegl1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libegl1-mesa-drivers (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgbm1 (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgl1-mesa-dri (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgl1-mesa-glx (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libglapi-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgles2-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgudev-1.0-0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libopenvg1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libpam-systemd (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-daemon0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-journal0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-login0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libudev1 (204-5ubuntu20.7) to 204-5ubuntu20.8
libwayland-egl1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libxatracker2 (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
systemd-services (204-5ubuntu20.7) to 204-5ubuntu20.8
udev (204-5ubuntu20.7) to 204-5ubuntu20.8
```

---

### Post by Bashing-om on 2014-11-14
oceola2; Hi !

Also report no problem:
> 
sysop@1404mini:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libopenvg1-mesa libwayland-egl1-mesa libxatracker2
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,937 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y


[INDENT][INDENT]the care a feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by oceola2 on 2014-11-15
The following packages, when trying to make the update using Synaptic, gave off the warning for the removal of a number of packages including Unity, Unity Scope, Totem and many of the related dependencies plus an install list of replacement files, mostly gnome but also some KDE files. Tried each file to see what kind of response I got before accepting the install and if the file showed removal and replacement moved on to the next. Installed the Gnome-calculator first followed by libgl1-mesa-dri , then libxatracker2 and libgbm1. Finally after a couple of tries was able to perform the entire remainder of the list without the notification of removal.
Repositories are standard repos Main,Universe, Multiverse and Restricted no third party like Get-deb or others but Independent and Canonical Partners are checked on the Other Software Tab. Packages warned of removal were extensive with notable things like Unity, Unity Control center and Totem and installs of a number of Gnome components and addition of Gnome Control center.
gnome-calculator (1:3.10.2-0ubuntu1.2) to 1:3.10.3-0ubuntu0.1.1
libegl1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libegl1-mesa-drivers (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgbm1 (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgl1-mesa-dri (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgl1-mesa-glx (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libglapi-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libgles2-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libopenvg1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libwayland-egl1-mesa (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2
libxatracker2 (10.1.3-0ubuntu0.1) to 10.1.3-0ubuntu0.2

**Performed the following updates on 11/13/2014 with no problems:**
gir1.2-gudev-1.0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libgudev-1.0-0 (1:204-5ubuntu20.7) to 1:204-5ubuntu20.8
libpam-systemd (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-daemon0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-journal0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libsystemd-login0 (204-5ubuntu20.7) to 204-5ubuntu20.8
libudev1 (204-5ubuntu20.7) to 204-5ubuntu20.8
systemd-services (204-5ubuntu20.7) to 204-5ubuntu20.8
udev (204-5ubuntu20.7) to 204-5ubuntu20.8

**The following on 11/11/2014 with no problems:**
curl (7.35.0-1ubuntu2.1) to 7.35.0-1ubuntu2.2
libcurl3 (7.35.0-1ubuntu2.1) to 7.35.0-1ubuntu2.2
libcurl3-gnutls (7.35.0-1ubuntu2.1) to 7.35.0-1ubuntu2.2

---

### Post by marksmarks on 2014-11-18
Had same “remove a bunch of stuff” issue here a few days ago (~11/14/14). 

[ATTACH=CONFIG]258065[/ATTACH]


Was scary.  I want to stay updated, yet can't afford to mess up my 'production' box!

So,...
Following advice above, I first updated libopenvg1-mesa by itself as it alone would not remove stuff.  


[ATTACH=CONFIG]258066[/ATTACH]


Then updated everything that was left all-at-once because they no longer wanted to remove everything.


[ATTACH=CONFIG]258067[/ATTACH]

Rebooted and everything remains fine.  Still have Unity Control Center, Totem, etc. installed.

---

