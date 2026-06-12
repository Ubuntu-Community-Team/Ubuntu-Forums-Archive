---
title: "Unable to install qt-sdk because of unmet dependencies"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by Spencer_Thompson on 2016-02-28
Hello. I am trying to install qt-sdk but it's telling me I have unmet dependencies. Is there any way to fix this? I am running Ubuntu 14.04.4. If you ask me to do something, please give some instructions as I don't know much about Ubuntu.

```
$ sudo apt-get install qt-sdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 qt-sdk : Depends: libqt4-opengl-dev but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by v3.xx on 2016-02-28
```
sudo apt-get -f install

```
That may clear it.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Are you running third party apps?  This is a major cause of conflicts.

```
ls /etc/apt/sources.list.d/*.list
```

Edit
And on a side note

I installed qt-sdk without issue on Mate 16.04.  A 900MB install :)  This is not much help with someone running Ubuntu 14.04, just thought you may like to know.

---

### Post by Spencer_Thompson on 2016-02-28
Ran the command but nothing changed. Still giving me the same result.

---

### Post by v3.xx on 2016-02-29
Did the first command show any errors?

The second command will list all third party software. Please post this.

Thanks

---

### Post by Spencer_Thompson on 2016-02-29
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ ls /etc/apt/sources.list.d/*.list
/etc/apt/sources.list.d/bumblebee-stable-trusty.list
/etc/apt/sources.list.d/commendsarnex-winedri3-trusty.list
/etc/apt/sources.list.d/dropbox.list
/etc/apt/sources.list.d/google-earth.list
/etc/apt/sources.list.d/oibaf-gallium-nine-trusty.list
/etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list
/etc/apt/sources.list.d/opera.list
/etc/apt/sources.list.d/opera-stable.list
/etc/apt/sources.list.d/playonlinux.list
/etc/apt/sources.list.d/spotify.list
/etc/apt/sources.list.d/steam.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list
/etc/apt/sources.list.d/wine-wine-builds-trusty.list
/etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list
```

---

### Post by v3.xx on 2016-02-29
Are all ppa's in use?  If not, remove unused ppa(s).  For the gui..

```
software-properties-gtk
```

Also check the regular sources list for any thing outside the ubuntu trusty sources.

```
cat /etc/apt/sources.list
```

You can also run "apt check" for broken dependencies.

```
sudo apt-get check
```

I suspect a conflict with a third party source, something I cannot test further on this end.

---

### Post by Spencer_Thompson on 2016-02-29
All the PPAs are in use, if by in use you mean the box next to each one is checked.
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.symnds.com/ubuntu/ trusty main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.symnds.com/ubuntu/ trusty-updates main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.symnds.com/ubuntu/ trusty universe
deb-src http://mirror.symnds.com/ubuntu/ trusty universe
deb http://mirror.symnds.com/ubuntu/ trusty-updates universe
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.symnds.com/ubuntu/ trusty multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty multiverse
deb http://mirror.symnds.com/ubuntu/ trusty-updates multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.symnds.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://mirror.symnds.com/ubuntu/ trusty-security main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty-security main restricted
deb http://mirror.symnds.com/ubuntu/ trusty-security universe
deb-src http://mirror.symnds.com/ubuntu/ trusty-security universe
deb http://mirror.symnds.com/ubuntu/ trusty-security multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
excalibur0126@spencer-Inspiron-660:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.symnds.com/ubuntu/ trusty main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.symnds.com/ubuntu/ trusty-updates main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.symnds.com/ubuntu/ trusty universe
deb-src http://mirror.symnds.com/ubuntu/ trusty universe
deb http://mirror.symnds.com/ubuntu/ trusty-updates universe
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.symnds.com/ubuntu/ trusty multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty multiverse
deb http://mirror.symnds.com/ubuntu/ trusty-updates multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.symnds.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://mirror.symnds.com/ubuntu/ trusty-security main restricted
deb-src http://mirror.symnds.com/ubuntu/ trusty-security main restricted
deb http://mirror.symnds.com/ubuntu/ trusty-security universe
deb-src http://mirror.symnds.com/ubuntu/ trusty-security universe
deb http://mirror.symnds.com/ubuntu/ trusty-security multiverse
deb-src http://mirror.symnds.com/ubuntu/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

---

### Post by v3.xx on 2016-02-29
Unless your building packages from source code, all deb-scr sources can be unchecked.

[ATTACH=CONFIG]267587[/ATTACH]
> 
All the PPAs are in use, if by in use you mean the box next to each one is checked.

Yes if you uncheck a ppa it will be disabled and no longer updated, but can be again activated by checking the box.  So all ppa's are active, but do you use all of them?

---

### Post by Spencer_Thompson on 2016-02-29
I use pretty much all of them, but I don't know what the Canonical Partners or Independent ppa's are. I unchecked the Source Code like you suggested.

---

### Post by v3.xx on 2016-03-01
> I don't know what the Canonical Partners or Independent ppa's are

[http://partners.ubuntu.com/programmes](http://partners.ubuntu.com/programmes)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

It's ok to have them checked.

You can try aptitude, it could give you some dependency options.

```
sudo aptitude install qt-sdk
```

---

### Post by Spencer_Thompson on 2016-03-01
Here's what comes up.
```
$ sudo aptitude install qt-sdk
The following NEW packages will be installed:
  cmake{a} cmake-data{a} libapr1{a} libaprutil1{a} libbotan-1.10-0{a} 
  libegl1-mesa-dev{a} libgl1-mesa-dev{ab} libgles2-mesa-dev{a} 
  libglu1-mesa-dev{a} libmirclient-dev{a} libmirprotobuf-dev{a} 
  libphonon-dev{a} libprotobuf-dev{a} libprotobuf-lite8{a} libqt4-dev{a} 
  libqt4-dev-bin{a} libqt4-opengl-dev{a} libqt5clucene5{a} 
  libqt5concurrent5{a} libqt5declarative5{a} libqt5designer5{a} 
  libqt5designercomponents5{a} libqt5help5{a} libqt5opengl5-dev{a} 
  libqt5quickparticles5{a} libqt5quicktest5{a} libqt5script5{a} 
  libqtwebkit-dev{a} libserf-1-1{a} libsvn1{a} libx11-xcb-dev{a} 
  libxcb-dri2-0-dev{a} libxcb-dri3-dev{a} libxcb-glx0-dev{a} 
  libxcb-present-dev{a} libxcb-randr0-dev{a} libxcb-shape0-dev{a} 
  libxcb-sync-dev{a} libxcb-xfixes0-dev{a} libxshmfence-dev{a} 
  libxxf86vm-dev{a} mircommon-dev{a} qmlscene{a} qt-sdk qt4-designer{a} 
  qt4-dev-tools{a} qt4-doc{a} qt4-doc-html{a} qt4-linguist-tools{a} 
  qt4-qmake{a} qt5-default{a} qt5-qmake{a} qtbase5-dev{a} 
  qtbase5-dev-tools{a} qtcreator{a} qtcreator-doc{a} 
  qtcreator-plugin-cmake{a} qtcreator-plugin-qnx{a} 
  qtcreator-plugin-remotelinux{a} qtcreator-plugin-valgrind{a} 
  qtdeclarative5-controls-plugin{a} qtdeclarative5-dev{a} 
  qtdeclarative5-quicklayouts-plugin{a} subversion{a} x11proto-dri2-dev{a} 
  x11proto-gl-dev{a} x11proto-xf86vidmode-dev{a} 
0 packages upgraded, 67 newly installed, 0 to remove and 0 not upgraded.
Need to get 184 MB of archives. After unpacking 459 MB will be used.
The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 10.1.3-0ubuntu0.6) but 11.2+gallium-nine~git1602220800.9e204a~gd~t is installed.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
The following actions will resolve these dependencies:


      Keep the following packages at their current version:                     
1)      libgl1-mesa-dev [Not Installed]                                         
2)      libglu1-mesa-dev [Not Installed]                                        
3)      libqt4-opengl-dev [Not Installed]                                       
4)      libqt5opengl5-dev [Not Installed]                                       
5)      qt-sdk [Not Installed]                                                  
6)      qt5-default [Not Installed]                                             
7)      qtbase5-dev [Not Installed]                                             
8)      qtdeclarative5-dev [Not Installed]                                      


      Leave the following dependencies unresolved:                              
9)      qtcreator recommends qt5-default                                        
10)     qtcreator recommends qtbase5-dev                                        
11)     qtcreator recommends qtdeclarative5-dev                                 
12)     libqt4-dev recommends libqt4-opengl-dev (= 4:4.8.5+git192-g085f851+dfsg-




Accept this solution? [Y/n/q/?]
```

---

### Post by v3.xx on 2016-03-01
> Typing y (or simply pressing enter) will accept the proposed solution. Typing n will display the “next best” solution.

 As with the main command-line prompt, you can perform a number of additional actions, including manually altering the states of packages, from the dependency resolution prompt. Type ? to see a complete list.

Typing q will abort the automatic resolver and allow you to resolve the dependencies manually.

[https://www.debian.org/doc/manuals/aptitude/ch01s02.en.html](https://www.debian.org/doc/manuals/aptitude/ch01s02.en.html)

---

### Post by Spencer_Thompson on 2016-03-01
First solution didn't get me anywhere, but the second solution installed it. Thanks for all the help!

---

### Post by v3.xx on 2016-03-01
I missed this, its getting late :)

The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 10.1.3-0ubuntu0.6)[COLOR="#FF0000"] but 11.2+gallium-nine~git1602220800.9e204a~gd~t is installed[/COLOR].

That would be your PPA.  Its the problem.

[http://packages.ubuntu.com/trusty-updates/libgl1-mesa-dev](http://packages.ubuntu.com/trusty-updates/libgl1-mesa-dev)

---

### Post by v3.xx on 2016-03-01
Funny :) aptitude to the rescue.  Glad that worked.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

