---
title: "unable to install python-notify, ubuntuone-client, ubuntu-desktop"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by abhishek709 on 2010-12-18
I am unable to install any packages which have dependency on python-notify. when i try to install ubuntuone-client, i get an error saying:
The following packages have unmet dependencies:
 ubuntuone-client : Depends: python-ubuntuone-client (= 1.4.5-0ubuntu1) but it is not going to be installed
E: Broken packages
When i try to install python-ubuntuone-client, i get an error:
The following packages have unmet dependencies:
 python-ubuntuone-client : Depends: python-notify but it is not going to be installed
E: Broken packages
python-notify installation gives the error:
The following packages have unmet dependencies:
 python-notify : Depends: python (< 2.6) but 2.6.6-2ubuntu2 is to be installed
E: Broken packages
If i try to install python2.5-minimal, apt says tht some 376 packages will be removed before python2.5-minimal is installed.
Please anyone explain to me y i m getting these error and is there any way to fix it.(I am using Ubuntu 10.10-Maverick Meerkat) 
Thanking you in advance.

---

### Post by ivanovnegro on 2010-12-18
Try to repair the broken packages within the Synaptic Package Manager. You open Synaptic and go to repair broken packages. Maybe it will help.

---

### Post by abhishek709 on 2010-12-18
it didnt work. i tried to fix the broken packages using apt also, no luck there either. i always get the dependency error. is thr any way to install python2.5 without removing the 376 packages (which include totem, rhythmbox, ubuntu software center,vlc, etc etc)??

---

### Post by ivanovnegro on 2010-12-18
> **abhishek709 said:**
> it didnt work. i tried to fix the broken packages using apt also, no luck there either. i always get the dependency error. is thr any way to install python2.5 without removing the 376 packages (which include totem, rhythmbox, ubuntu software center,vlc, etc etc)??

Did you try it also with this commands?

```
sudo dpkg --configure -a
sudo apt-get install -f

```

---

### Post by abhishek709 on 2010-12-18
yes i tried those. the thing is i am able to install other packages. i just installed a new package and the installation was fine. but when i try to install ubuntu one, i start getting those dependency errors.

---

### Post by ivanovnegro on 2010-12-18
> **abhishek709 said:**
> yes i tried those. the thing is i am able to install other packages. i just installed a new package and the installation was fine. but when i try to install ubuntu one, i start getting those dependency errors.

Ok, now I hope somebody could join us to solve the problem as Im not sure what is happening and Im asking me how is it possible that you have not Ubuntu One preinstalled, you removed it?
Maybe you could put the output of your Sources List to see if there is something wrong.

---

### Post by abhishek709 on 2010-12-18
here is my source.list:
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main
deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free
deb-src [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main

---

### Post by abhishek709 on 2010-12-18
i didnt remove anything. i was trying to install the package app-install-data.  dpkg hung during installation. i did tht rm /var/lib/dpkg/lock and the dpkg --configure -a. after tht i ran synaptic and tried to fix the broken package. i didnt see tht it said it will remove certain packages and i ran it. so it removed ubuntu one, totem, vlc, deluge, rhythmbox, and many other packages. i was able to reinstall most of them but i can't install ubuntuone and deluge. and tht python-notify package also.

---

### Post by ivanovnegro on 2010-12-18
> **abhishek709 said:**
> here is my source.list:


deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main

Ok, what is doing Debian Lenny in this list?
This could be the culprit.
You mixed your repositoty with the ones of Debian stable.

---

### Post by abhishek709 on 2010-12-18
wow. it fixed it. i removed debian lenny from the list and its fine now. ubuntuone installation just completed.
Thanks a lot ivanovnegro.

---

### Post by ivanovnegro on 2010-12-18
> **abhishek709 said:**
> wow. it fixed it. i removed debian lenny from the list and its fine now. ubuntuone installation just completed.
Thanks a lot ivanovnegro.

No problem, glad, you fixed it and remember, do not mix your reposotories with other distros.

---

### Post by abhishek709 on 2010-12-18
ya sure man. i might have copied some terminal command from the net and added it. thanks again.

---

