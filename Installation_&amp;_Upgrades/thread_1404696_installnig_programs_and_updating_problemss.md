---
title: "installnig programs and updating problemss"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by primo6711 on 2010-02-11
i have ubuntu karmic 9.10 and when i try to update anything or install anything the a very similar error occurs. "(Reading database . . . 55%dpkg: unrecoverable fatal error , aborting: files list file for package `com.palm.net.precoddr.fcoaster' contains empty filename

it repeats this message 3 times then gives up i believe. can someone please help me? thank you all very much

---

### Post by Satoru-san on 2010-02-11
Can you please post 2 things for me.

I need to see the entire log and I also need to see your /etc/apt/sources.list 

and paste them here.

---

### Post by primo6711 on 2010-02-12
Reading database . . . 55%dpkg: unrecoverable fatal error, aborting: files list file for package `com.palm.net.precoder.fcoaster' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. trying to recover:

---

### Post by primo6711 on 2010-02-12
i typed /etc/apt/sources.list in the terminal and it said permission denied. i am the admin of the computer so i should have all permissions right? i am a linux newbie so bare with me. please explain exactly what i need to do to give you the information you need. shortcut keys work in some place but not others..... trying t get used to this

---

### Post by LOLbuntu on 2010-02-12
type sudo gedit /etc/apt/sources.list

---

### Post by Satoru-san on 2010-02-12
> **LOLbuntu said:**
> type sudo gedit /etc/apt/sources.list
That might fail, you can do this
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by primo6711 on 2010-02-12
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe #Added by software-properties
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by Satoru-san on 2010-02-12
Thank you.

Now I need you to install the software again, only this time, I need you to do it from the terminal, this is because the gui doesnt have any detailed errors.

```
sudo apt-get install <package>
```

if you dont know what <package> is called do this

```
apt-cache search <package name>
```

---

### Post by primo6711 on 2010-02-12
blessed@blessed-laptop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

also this one

blessed@blessed-laptop:~$ sudo apt-get install cairo-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cairo-dock-core cairo-dock-data cairo-dock-plug-ins cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration curl libgtkglext1 xdotool
The following NEW packages will be installed:
  cairo-dock cairo-dock-core cairo-dock-data cairo-dock-plug-ins
  cairo-dock-plug-ins-data cairo-dock-plug-ins-integration curl libgtkglext1
  xdotool
0 upgraded, 9 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/6,174kB of archives.
After this operation, 13.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package cairo-dock-data.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `com.palm.net.precoder.fcoaster' contains empty filename

i don't know how to do updates in terminal so i can't show you that, hopefully this is enough. thank you

---

### Post by primo6711 on 2010-02-12
blessed@blessed-laptop:~$ sudo apt-get install cairo-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cairo-dock-core cairo-dock-data cairo-dock-plug-ins cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration curl libgtkglext1 xdotool
The following NEW packages will be installed:
  cairo-dock cairo-dock-core cairo-dock-data cairo-dock-plug-ins
  cairo-dock-plug-ins-data cairo-dock-plug-ins-integration curl libgtkglext1
  xdotool
0 upgraded, 9 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/6,174kB of archives.
After this operation, 13.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package cairo-dock-data.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `com.palm.net.precoder.fcoaster' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
blessed@blessed-laptop:~$

---

### Post by primo6711 on 2010-02-12
any ideas people?

---

### Post by primo6711 on 2010-02-12
is this curable?

---

### Post by primo6711 on 2010-02-14
its been solved

[http://www.bleepingcomputer.com/forums/index.php?showtopic=295396&st=0&gopid=1629145&#entry1629145](http://www.bleepingcomputer.com/forums/index.php?showtopic=295396&st=0&gopid=1629145&#entry1629145)

---

