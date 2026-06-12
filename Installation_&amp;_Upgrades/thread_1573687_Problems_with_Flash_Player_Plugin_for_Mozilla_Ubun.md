---
title: "Problems with Flash Player Plugin for Mozilla Ubuntu 10.04 AMD64"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by baseballa51 on 2010-09-13
Hello to all!   ):P

I am a new member to the official Ubuntu community and have some inquiries regarding my *Flash Player Plugin.*

**_Setup:_** Ubuntu 10.04 (Fresh Clean Install) AMD64 Desktop - Using Firefox 3.6.9 with Flash Player Plugin

**_Problem:_** I can watch videos but cannot interface with the plugin. I.E. I cannot change volume, fullscreen, progress bar adjust, etc.

After researching for many How To's and install scripts I finally came across one that worked for my particular setup:
 sudo apt-get install flashplugin-nonfree

**_I got the script from the following link:_**
file:///media/Pictures/Backup/setups/Linux/Ubuntu%2010.04%20Drivers%20and%20Utilities/showthread.php.html

This installed successfully and I can watch videos but cannot interface with the plugin. I.E. I cannot change volume, fullscreen, progress bar adjust, etc.

I read that changes are in progress to update the 64 bit Flash Plugin for Mozilla, could this be a bug people have reported?

Any support is greatly appreciated. 

Thank you

---

### Post by sikander3786 on 2010-09-13
For possible issues with Flash:
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

### Post by garvinrick4 on 2010-09-13
You know just for the hell of it put this code in and make sure you got all your flash, java, codecs and such. If you already got it will tell you so no harm no foul.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by garvinrick4 on 2010-09-13
This is a sources list. This is maverick just make sure you have all your repositorys
turned on. If you need a lucid post so. Or go to System/Administration to Software Sources and turn em on. Close and will reload for you.
Every one without a # (comment) is a working repository. deb-src means source code, do not really need it but do not worry about it. 
```
gedit /etc/apt/sources.list
``````
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha amd64 (20100911)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free
```gksudo gedit /etc/apt/sources.list

puts you in as root and you can make changes and save. Be carefull in root if you are unsure ask.

---

### Post by baseballa51 on 2010-09-13
Thank everyone for the useful information. This fixed my Flash problem and I'm sure prevented another search for information later. Thank You!

---

