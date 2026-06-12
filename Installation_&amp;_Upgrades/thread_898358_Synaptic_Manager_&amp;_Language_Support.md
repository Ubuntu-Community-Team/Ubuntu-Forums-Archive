---
title: "Synaptic Manager &amp; Language Support"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by pacchiee on 2008-08-23
Hello Friends,

This is my first post in Ubuntu Forums. I have been using Ubuntu 8.04 for the past 15 days and started loving it. It is fine on my laptop but the desktop machine being a bit old, found it to be too heavy. So, read about Xubuntu 8.04.1 - its for low powerful machines and installed it on my desktop machine.

Now, I am not able to use Synaptic Package Manager to install additional software in Xubuntu. For example, if I search for apache2 or php5, no results match. I even tried from terminal 'sudo apt-get install apache2' which failed.

When I went to Applications -> System -> Language Support, only English is listed and selected. As in Ubuntu 8.04, I am not able to select a language of my choice and install it. But, when I boot the Live CD, all languages are listed as in Ubuntu.

Is it not possible to add software like apache php vlc wine in Xubuntu as we do in Ubuntu? Also, I want to know if Xubuntu doesn't support all the languages as in Ubuntu.

Thanks in Advance.

---

### Post by Partyboi2 on 2008-08-23
You should be able to install all those programs. Can you post the output from the terminal when you try and install a program. One thing you could check is that you have the ubuntu repo's enabled. You can do this by going to Applications>System>Software Sources on the first tab make sure they are all ticked except source code.

---

### Post by pacchiee on 2008-08-23
I checked the repositories, everything is checked except source code.

In the terminal I typed, 'sudo apt-get install apache2' - output follows:

$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2 is not available, but is referred by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package apache2 has no installation candidate
$

Any clue??

---

### Post by Partyboi2 on 2008-08-23
What server are you using? Maybe try changing your download server in Software Sources.

---

### Post by pacchiee on 2008-08-24
I am using Indian Update Server; changing it made no difference. With the same Indian Update Server, I am able to install softwares from Xubuntu on my laptop, which I have installed as a Xubuntu-Desktop upgrade from Ubuntu installation.

When I downloaded the ISO image to burn the boot disk, it was the xubuntu-8.04.1-desktop-i386.iso. Should I actually download xubuntu-8.04.1-alternate-i386.iso image? Are there chances of such problems if we select a wrong ISO image? The Ubuntu am using successfully was burnt from ubuntu-8.04-alternate-i386.iso image.

---

### Post by pacchiee on 2008-08-24
Forgot to mention, its Intel Pentium inside.

---

### Post by Partyboi2 on 2008-08-24
You should be able to install those packages regardless if you installed xubuntu from the live cd or the alternate cd. Can you open a terminal again and post the output to
```
sudo apt-get update
```and 
```
cat /etc/apt/sources.list
```

---

### Post by pacchiee on 2008-08-24
sudo apt-get update
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages [4297kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               

.. got a big list of updates which I have cut short


cat /etc/apt/sources.list
#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Partyboi2 on 2008-08-24
Well your sources.list seems  to be in order. At the moment I am at a loss to why you cannot install packages. Maybe someone else might know.

---

### Post by crgutierrez on 2008-08-24
Same problem, but no, nobody awake to help out.................this is BAD news

---

### Post by pacchiee on 2008-08-25
Phew!

I just did a 'clean' re-installation of Xubuntu using the 'same' installer CD and 'same' machine, to my pleasant surprise everything works!!

Thanks so much Partyboi2 for all your time and patience in guiding me through.

---

### Post by pacchiee on 2008-08-25
Oops!

One problem seems to be solved and the other pops up :o(

I have two hard disks in my desktop machine, which were shown as sda and sdb while I installed Xubuntu. I did the installation on sdb as sda was used to run windows. Now, when I boot the machine using Xubuntu the windows partitions/hard disk is not mounted. Places tab doesn't have the 'computer' option listed.

In the previous installation when there was a problem with Synaptic PM and Lang Sup, there was no issues mounting windows partition.

Please help.

---

