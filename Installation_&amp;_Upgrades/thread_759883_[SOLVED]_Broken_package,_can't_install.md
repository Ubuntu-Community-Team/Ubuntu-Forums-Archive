---
title: "[SOLVED] Broken package, can't install"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2008-04-19
I'm tried to install Project Looking Glass but my computer froze during the installation process and I had to shut it down. Now whenever I try to reinstall the packages I get a "broken" package eror message.

root@Mixed-up:~# apt-get install lg3d-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxalan110 libqt3-mt libaudio2 libxerces27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lg3d-java3d lg3d-jdk
The following NEW packages will be installed:
  lg3d-core lg3d-java3d lg3d-jdk
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/141MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  lg3d-jdk lg3d-java3d lg3d-core
Install these packages without verification [y/N]? y
Preconfiguring packages ...
lg3d-jdk failed to preconfigure, with exit status 1
(Reading database ... 122480 files and directories currently installed.)
Unpacking lg3d-jdk (from .../lg3d-jdk_1.6.0+b104_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package lg3d-java3d.
Unpacking lg3d-java3d (from .../lg3d-java3d_1.5.0_i386.deb) ...
Unpacking lg3d-core (from .../lg3d-core_1.0.1%5fdev_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lg3d-core_1.0.1%5fdev_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb
 /var/cache/apt/archives/lg3d-core_1.0.1%5fdev_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mixed-up:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  lg3d-java3d: Depends: lg3d-jdk (>= 1.5.0) but it is not installed
E: Unmet dependencies. Try using -f.
root@Mixed-up:~# apt-get -f install lg3d-java3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-java3d is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  lg3d-java3d: Depends: lg3d-jdk (>= 1.5.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Mixed-up:~# apt-get -f instal lg3d-jdk
E: Invalid operation instal
root@Mixed-up:~# apt-get -f install lg3d-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxalan110 libqt3-mt libaudio2 libxerces27
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  lg3d-jdk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/73.9MB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  lg3d-jdk
Install these packages without verification [y/N]? Y
Preconfiguring packages ...
lg3d-jdk failed to preconfigure, with exit status 1
(Reading database ... 122490 files and directories currently installed.)
Unpacking lg3d-jdk (from .../lg3d-jdk_1.6.0+b104_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by brownknight on 2008-04-19
> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Im just a noob but the above says  try apt-get -f install with no packages so shouldnt it be typed in terminal as:

apt-get -f install

and not

apt-get -f install lg3d-jdk 

I dont know if that will make any difference...

---

### Post by absolutezero1287 on 2008-04-19
Brownknight: I tried apt-get -f and it didn't work.


Here's the result of cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
[B]deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib[/B]


The ones in bold are the repos for Project Looking Glass.
[http://www.sun.com/software/looking_glass/](http://www.sun.com/software/looking_glass/)

---

### Post by brownknight on 2008-04-20
I saw a post that says use only of the three repos for looking glass (not all of them). Use which ever one you prefer. Check this link out if you want to verify what I read:

[http://www.ubuntugeek.com/install-sun-looking-glass-desktop-environment-in-ubuntu.html](http://www.ubuntugeek.com/install-sun-looking-glass-desktop-environment-in-ubuntu.html)

---

### Post by absolutezero1287 on 2008-04-20
Update! Compiled it from source and almost finished except for one problem:

leonardo@Mixed-up:~$ sudo -s
[sudo] password for leonardo: 
root@Mixed-up:~# cd /usr/share/lg3d/bin
root@Mixed-up:/usr/share/lg3d/bin# ./postinstall
./../usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
./../usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
./../usr/share/lg3d/bin/postinstall: line 43: cd: ./../usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory'

postinstall is a script that you have to run, you guessed it, post-install. I'm not 100% sure what it's trying to do but I figure that even if I create the directories that it's looking for, it won't solve the problem.

---

### Post by Partyboi2 on 2008-04-21
Open a terminal, change into the /bin directory
```
cd /bin
```
then
```
sudo nano arch
```
add this to the file
```
 uname -m
```
then save
Ctrl+o
enter
then exit
Ctrl+x
then finally
```
 sudo chmod +x arch
```

---

### Post by absolutezero1287 on 2008-04-21
I'm gonna give it a shot, thanks.

---

### Post by absolutezero1287 on 2008-07-04
That did the trick. Problem solved!

---

