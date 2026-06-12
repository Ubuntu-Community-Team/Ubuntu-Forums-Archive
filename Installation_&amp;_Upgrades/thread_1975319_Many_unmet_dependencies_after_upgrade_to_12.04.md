---
title: "Many unmet dependencies after upgrade to 12.04"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by jabrown65 on 2012-05-07
After upgrading initially from 10.04, my system complained of many upmet dependencies. I kept upgrading to each successive version in the hope the problems would resolve themeselves. With each version it seems to get a little better, but I have got to 12.04 and (even after apt-get clean) apr-get upgrade produces the following list:


Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libqt4-declarative : Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-designer : Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                   Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                   Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-help : Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
               Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
               Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-opengl : Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-qt3support : Depends: libqt4-network (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                     Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                     Depends: libqt4-xml (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                     Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-scripttools : Depends: libqt4-script (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqt4-svg : Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 libqtgui4 : Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is installed
 update-manager : Depends: update-manager-core (= 1:0.156.14) but 1:0.156.14.1 is installed

Things I have notice which don't work include Terminal, cutting and pasting in Xterm, and MythTV

Errors in earlier upgrades included having multiple sources, and 3rd party sources, so I removed all extra repositories, which seemed to fix some problems, but could that have resulted in these errors? It still produces the list of Duplicate sources.list errors but I can't cut and paste from xterm so can't show them here. (The above output was obtained using apt-get upgrade>junk.txt then cutting and pasting from junk.txt, but this doesn't work for all output).

My /etc/apt/sources.txt contains:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) precise main universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) precise main universe #Added by software-properties
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe

John

---

### Post by zvacet on 2012-05-08
```
sudo apt-get -f install
```

---

### Post by jabrown65 on 2012-05-08
Thanks for your reply. Unfortunately if I attempt to use *sudo apt-get -f install* to try and install any of the missing dependencies it results in the same list of errors.

---

### Post by zvacet on 2012-05-08
Try on by one (or s gruop)

```
sudo dpkg --configure update-manager
```

```
sudo dpkg --configure libqt4-network
```

---

### Post by jabrown65 on 2012-05-12
Thanks! Progress! This worked for the listed packages:
dpkg --configure libgksu2-0 libgconf2-4 gconf2 gconf-service gconf-service-backend

However, it doesn't work for the other packages, eg.

dpkg --configure libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-xmlpatterns libqtcore4 libqtgui4

... produced the output shown in *screenshot1.jpg*

Terminal still won't work and I still can't cut and paste in Xterm. Actually lots of things doen't work in the GUI, sucj as unable to select the tools I want in GIMP, and the GUI seems to be a mix of classic and unit, with menu bars overlaping each other in the top left hand part of the screen. A bit of a mess really! Getting the attached screenshots was a bit of a challenge! I think I'll do a clean install eventually, but would like to get it working now if I can so I can do some things with my data that will make it easier to recover after a clean install.

*screenshot2.jpg* shows the duplicate sources errors I am getting following *apt-get update* as well as the arros I get following *apt-get upgrade*.

Let me know if there are any log files that I should be checking. Please make sure you provide the fully path if possible.

Further assistance would be greatly appreciated!

Thanks,

John

---

### Post by jadtech on 2012-05-12
the version of that library you need is not there to install or configure the older version is still there  .. 

```
 sudo apt-get update

sudo apt-get upgrade -f


```
see if that helps
libqt4 4:4.8.1-0ubuntu4 is needed and libqt4 4:4.81-0ubuntu1 is installed 

the end of the list in the first screen shot is full of  denpendancy issues the same

anhy how the upgrade -f should build the dependancy list and down load and install everything needed or hopefully enough to get 12.4 its self working like it should  from there  maybe other update  will get the other programs going  some may even need to be uninstalled purged and reinstalled ..

clean install is preferable to many upgrades from 10.4 to 12.4  this plan is nearly assured to break something :)

---

### Post by debussyfields on 2012-05-13
I've followed all the advice featured on this particular post, but it doesn't look good here.

Here is the final bit of info, pasted from Terminal, which seems to summarise my dilemma:


Errors were encountered while processing:
 libgdata1.9-cil
 libgkeyfile1.0-cil
 libgudev1.0-cil
 libmono-zeroconf1.0-cil
 libnotify0.4-cil
 libtaglib2.0-cil
 banshee
 banshee-extension-soundmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any advice would be greatly appreciated.
Thanks.

---

### Post by jadtech on 2012-05-13
at this point you might try again

```
 
sudo apt-get -f install

configure -a

```

i dont understand alot about this  how ever 

as I search around  it seems  at this point this "libmono-zeroconf1.0-cil"

seems to be at the root of  the problem need to get this to install most likely would help lots ..
check this link for info 


in all honesty if it was me I would get  booted in live disk pull all the  files  pictures music what ever is important and install 12.04 from disk .. most likely there is some one here who  understands  whats going on here to maybe get it going   I say never give up its all an adventure   learning   just  get  backed up what you can  incase :) 

[https://launchpad.net/ubuntu/precise/i386/libmono-zeroconf1.0-cil](https://launchpad.net/ubuntu/precise/i386/libmono-zeroconf1.0-cil)

---

