---
title: "problem with x-server"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by sick_bug on 2008-07-10
im using ubuntu 8.04
i installed glib 2.14.6 and after that many gui applications stop working.
After rebooting are curser keeps showing busy pointer but the login prompt doesn't come up.:confused:

---

### Post by PmDematagoda on 2008-07-11
How did you install GLib? Was it by compiling it?

---

### Post by sick_bug on 2008-07-11
I downloaded package glib-2.14.6.tar.gz
after that
gzip -cd glib-2.14.6.tar.gz | tar xvf - 
cd glib-2.14.6                          
  % ./configure                         
  % make                                


  % rm -rf /install-prefix/include/glib.h /install-prefix/include/gmodule.h
  % make install                           

after that
when i tried to open nautilus it didnt open....
so i rebooted
and then even login screen is not coming but system is working fine in command line mode

---

### Post by PmDematagoda on 2008-07-11
I think the version of GLib you installed may have conflicted with the other packages since your version is 2.14.6 while the one in the Hardy repositories is 2.16.3. So try and reinstall GLib through the repositories with:-
```
sudo apt-get install --reinstall libglib2.0-0
```

---

### Post by sick_bug on 2008-07-14
no the problem is still coming.
Is there any way i can restore or fix the gnome desktop.
Because I installed mant packages after that so cant figure out which packagke created the problem.

---

### Post by elcid007 on 2008-07-14
you could try reinstalling your gnome desktop enviorment 
first try fixing broken dependencies 

sudo apt-get install -f

then use this 

sudo apt-get install --reinstall gnome-desktop-environment

---

### Post by sick_bug on 2008-07-14
I tried but following problem is coming:

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-desktop-environment: Depends: gnome-keyring-manager (>= 2.20.0) but it is not installable

---

### Post by PmDematagoda on 2008-07-15
Can you please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by sick_bug on 2008-07-15
here's the output for /etc/apt/sources.list :-

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by PmDematagoda on 2008-07-16
Try removing the package in question and installing ubuntu-desktop with:-
```
sudo apt-get remove gnome-desktop-environment && sudo apt-get install ubuntu-desktop
```
keep in mind that the command is to be done with the X-Server first shut down and you being logged into a tty which can be done by pressing Ctrl+Alt+F1, the X-Server can be shutdown with:-
```
sudo /etc/init.d/gdm stop 
```

---

### Post by sick_bug on 2008-07-17
I reinstalled ubuntu desktop but the problem still persists.

---

