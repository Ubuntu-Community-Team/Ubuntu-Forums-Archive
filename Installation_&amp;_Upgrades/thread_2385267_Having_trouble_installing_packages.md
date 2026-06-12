---
title: "Having trouble installing packages"
date: 2018-02-18
forum: Installation &amp; Upgrades
---

### Post by dg658 on 2018-02-18
I am attempting to install tesseract-ocr and receive these messages:

```
]dan@dan-All-Series:~/anaconda$ sudo apt-get install tesseract-ocr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgif4 liblept4 libopenjp2-7 libtesseract3v5 tesseract-ocr-eng
  tesseract-ocr-equ tesseract-ocr-osd
The following NEW packages will be installed:
  libgif4 liblept4 libopenjp2-7 libtesseract3v5 tesseract-ocr
  tesseract-ocr-eng tesseract-ocr-equ tesseract-ocr-osd
0 upgraded, 8 newly installed, 0 to remove and 235 not upgraded.
Need to get 2,158 kB/14.7 MB of archives.
After this operation, 58.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libgif4 libopenjp2-7 liblept4 libtesseract3v5 tesseract-ocr-eng
  tesseract-ocr-osd tesseract-ocr-equ tesseract-ocr
Install these packages without verification? [y/N] y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/universe liblept4 i386 1.72-3
  404  Not Found [IP: 91.189.91.26 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/universe libtesseract3v5 i386 3.04.00-5ubuntu1
  404  Not Found [IP: 91.189.91.26 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/universe tesseract-ocr i386 3.04.00-5ubuntu1
  404  Not Found [IP: 91.189.91.26 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/leptonlib/liblept4_1.72-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/leptonlib/liblept4_1.72-3_i386.deb)  404  Not Found [IP: 91.189.91.26 80]

E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tesseract/libtesseract3v5_3.04.00-5ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tesseract/libtesseract3v5_3.04.00-5ubuntu1_i386.deb)  404  Not Found [IP: 91.189.91.26 80]

E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tesseract/tesseract-ocr_3.04.00-5ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tesseract/tesseract-ocr_3.04.00-5ubuntu1_i386.deb)  404  Not Found [IP: 91.189.91.26 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

This is what I see with cat sources:
```

# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)]/ vivid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.[http://radius-it.eu/](http://radius-it.eu/)
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
```

Thanks in advance for any advice.

---

### Post by coffeecat on 2018-02-18
Welcome to the forum.

You appear to be running Ubuntu 15.10 (Wily), upgraded from a 15.04 (Vivid) system. Ubuntu 15.10 went end of life and became unsupported in July 2016. Since then the repositories have been closed, and there have been no updates.

Just to confirm that you are indeed running 15.10, please post the output of this terminal command:

```
cat /etc/lsb-release
```

By the way, please post terminal output between BBCode code tags, not quote tags, to retain formatting. I've edited your first post to change the quote tags to code tags.

---

### Post by oldfred on 2018-02-18
Wily has expired. You need to upgrade to a current version.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) 
    
```
 Version     Code name         Release date     Supported until     Kernel Version                                
15.10         Wily Werewolf         2015-10-22[227    ]     2016-07         4.2[245] 


```

If you do not want to upgrade every 9 months better to use the LTS versions which are supported for 5 years.

---

### Post by dg658 on 2018-02-18
Here is the version. Does this mean I need to upgrade to the latest Ubuntu before doing anything?

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"
```

---

### Post by oldfred on 2018-02-18
Yes

Be sure to have good backups whether you elect to upgrade to 16.04 or do a new install.

If upgrading, comment out any ppa, and turn off any proprietary drivers. They can conflict with upgrade and cause upgrade to fail. You can reinstall after upgrade if desired.

---

