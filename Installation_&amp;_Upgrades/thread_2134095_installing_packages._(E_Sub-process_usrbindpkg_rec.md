---
title: "installing packages. (E: Sub-process /usr/bin/dpkg received a segmentat...)"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by fridgecow on 2013-04-10
When trying to install packages or just generally do an upgrade:
>   istom@isToms-PC:~$ sudo apt-get install bum[sudo] password for istom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
Suggested packages:
  menu-l10n
The following NEW packages will be installed
  bum menu
0 upgraded, 2 newly installed, 0 to remove and 32 not upgraded.
Need to get 0 B/531 kB of archives.
After this operation, 2,328 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Sub-process /usr/bin/dpkg received a segmentation fault.


Results of dpkg --configure -a: just "Segmentation fault"

Ubuntu 12.04 LTS, was fresh installed only a few weeks ago.

---

### Post by fridgecow on 2013-04-11
Bump?

---

### Post by Bashing-om on 2013-04-11
fridgecow;
I have never had experience with a seg fault on my own system, But I will try and assist, if nothing else get some info for others to look at.
Before attacking the file system at large, let's see what condition the package manager is in: terminal codes:
```

dpkg --audit
sudo apt-get update
sudo apt-get upgrade
```[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by fridgecow on 2013-04-11
>  istom@isToms-PC:~$ sudo dpkg --audit
istom@isToms-PC:~$ dpkg --audit
Segmentation fault


"sudo apt-get update" goes like usual, no errors at all. "sudo apt-get upgrade":
>  istom@isToms-PC:~$ The following packages have been kept back:  linux-headers-generic-lts-quantal linux-image-generic-lts-quantal
The following packages will be upgraded:
  bash firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  flashplugin-installer gir1.2-dee-1.0 libavcodec53 libavformat53
  libavutil-extra-51 libdee-1.0-4 libgnomekbd-common libgnomekbd7
  libjack-jackd2-0 libnautilus-extension1a libnm-gtk-common libnm-gtk0
  libpostproc52 libswscale2 linux-generic-lts-quantal linux-libc-dev nautilus
  nautilus-data network-manager-gnome simple-scan thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us
30 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/59.4 MB of archives.
After this operation, 1,914 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.

And that's all.

---

### Post by Bashing-om on 2013-04-11
fridgecow;
We know the system it's self is operational thus maybe only dpkg has a problem;
See what results:
```


sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```does clearing the cache help ?[INDENT=2]
regards

[/INDENT]

---

### Post by fridgecow on 2013-04-12
Well my system must be REALLY messed up, because that doesn't help either. Exactly the same output as before

---

### Post by Bashing-om on 2013-04-13
fridgecow;
Doesn't seem too messed up. Your system is operational with the exception of package management. However, a seg-fault to me is reason for concern.  
Firstly, let's see if we can get the kernel to upgrade.
terminal code:
```
sudo apt-get dist-upgrade
``` "dist-upgrade" uses the package manager's smart mode to resolve dependencies.
Now what is the package manager's complaint and of what ?[INDENT=3]
try'n to help

[/INDENT]

---

### Post by fridgecow on 2013-04-13
```
 [sudo] password for istom: Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-3.5.0-27 linux-headers-3.5.0-27-generic
  linux-image-3.5.0-27-generic
The following packages will be upgraded:
  bash firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  flashplugin-installer gir1.2-dee-1.0 libavcodec53 libavformat53
  libavutil-extra-51 libdee-1.0-4 libgnomekbd-common libgnomekbd7
  libjack-jackd2-0 libnautilus-extension1a libnm-gtk-common libnm-gtk0
  libpostproc52 libswscale2 linux-generic-lts-quantal
  linux-headers-generic-lts-quantal linux-image-generic-lts-quantal
  linux-libc-dev nautilus nautilus-data network-manager-gnome simple-scan
  thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us
32 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/113 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Extract templates from packages: 100%
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.
```

Same as just "upgrade", really.

---

### Post by Bashing-om on 2013-04-14
fridgecow;
I have been unable, to this time, to find a means to determine which program is violating memory. If you were to individually install those 32 updates might get enough information to focus on the problem.
```
sudo apt-get install bash
``` Doing it the hard way is not the ubuntu way, I just do not know of a better way.
Go down the list of the remainder of the pending updates and advise what results.
[INDENT]
hope this helps

[/INDENT]

---

### Post by fridgecow on 2013-04-17
Not even that works.
>  istom@isToms-PC:~$ sudo apt-get install bash[sudo] password for istom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bash-doc
The following packages will be upgraded:
  bash
1 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
Need to get 0 B/616 kB of archives.
After this operation, 12.3 kB disk space will be freed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


---

### Post by Bashing-om on 2013-04-17
fridgecow;
First try and see what state dpkg is in:
```
sudo dpkg --configure -a 
```
Then let's try this approach to identify the offending package:
```
sudo dpkg -l | grep -v ^ii 
```
> The "dpkg -l" part of the command lists all of the installed packages in  a table format. The first column of the table outlines the status of  the package, for example if it is installed correctly etc. The second  part of the command "grep -v ^ii" outputs any line that does not start  with the letters ii. By passing the output of the "dpkg -l" command to  the grep command I was able to get a list of all packages that were  listed as not being correctly installed. That is, those packages that  didn't have a status of "ii". I was then able to use this command to  remove the offending package where [package-name] was the name of the  package.
Then if identified:
```
sudo dpkg --purge remove [package-name] 
```[INDENT]
see what results

[/INDENT]

---

### Post by fridgecow on 2013-04-18
I would probably purge the results, except there are a lot, including linux-images

```
 istom@isToms-PC:~$ sudo dpkg -l | grep -v ^iiDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                                 Description
+++-=========================================-=======================================-========================================================================================================================================================================================================================================
rc  deja-dup                                  22.0-0ubuntu3                           Back up your files
rc  docbook-xml                               4.5-7ubuntu1                            standard XML documentation system for software and systems
rc  docbook-xsl                               1.76.1+dfsg-1ubuntu1                    stylesheets for processing DocBook XML to various output formats
rc  kate                                      4:4.8.5-0ubuntu0.1                      K Advanced Text Editor
rc  kate-data                                 4:4.8.5-0ubuntu0.1                      shared data files for kate
rc  kde-runtime                               4:4.8.5-0ubuntu0.1                      runtime components from the official KDE release
rc  kde-runtime-data                          4:4.8.5-0ubuntu0.1                      shared data files for the KDE base runtime module
rc  kdelibs5-data                             4:4.8.5-0ubuntu0.1                      core shared data for all KDE Applications
rc  libattica0.3                              0.3.0-0ubuntu2                          a Qt library that implements the Open Collaboration Services API
rc  libavutil51                               4:0.8.5-0ubuntu0.12.04.1                Libav utility library
rc  libclucene0ldbl                           0.9.21b-2                               library for full-featured text search engine (runtime)
rc  libdlrestrictions1                        0.14.2ubuntu5                           library that implements library compatibility checks for dlopen()
rc  libdrm-nouveau2                           2.4.39-0ubuntu0.1                       Userspace interface to nouveau-specific kernel DRM services -- runtime
rc  libgl1-mesa-dri-lts-quantal               9.0-0ubuntu1~precise4                   free implementation of the OpenGL API -- DRI modules
rc  libgl1-mesa-glx-lts-quantal               9.0-0ubuntu1~precise4                   free implementation of the OpenGL API -- GLX runtime
rc  libglapi-mesa-lts-quantal                 9.0-0ubuntu1~precise4                   free implementation of the GL API -- shared library
rc  libgsoap1                                 2.8.4-2                                 Runtime libraries for gSOAP
rc  libkateinterfaces4                        4:4.8.5-0ubuntu0.1                      kate plugin interface library
rc  libkatepartinterfaces4                    4:4.8.5-0ubuntu0.1                      kate part library
rc  libkcmutils4                              4:4.8.5-0ubuntu0.1                      utility classes for using KCM modules
rc  libkde3support4                           4:4.8.5-0ubuntu0.1                      KDE 3 Support Library for the KDE 4 Platform
rc  libkdeclarative5                          4:4.8.5-0ubuntu0.1                      Declarative library for plasma
rc  libkdecore5                               4:4.8.5-0ubuntu0.1                      KDE Platform Core Library
rc  libkdesu5                                 4:4.8.5-0ubuntu0.1                      Console-mode Authentication Library for the KDE Platform
rc  libkdeui5                                 4:4.8.5-0ubuntu0.1                      KDE Platform User Interface Library
rc  libkdewebkit5                             4:4.8.5-0ubuntu0.1                      KDE WebKit Library
rc  libkdnssd4                                4:4.8.5-0ubuntu0.1                      DNS-SD Protocol Library for the KDE Platform
rc  libkemoticons4                            4:4.8.5-0ubuntu0.1                      utility classes to deal with emoticon themes
rc  libkfile4                                 4:4.8.5-0ubuntu0.1                      File Selection Dialog Library for KDE Platform
rc  libkhtml5                                 4:4.8.5-0ubuntu0.1                      KHTML Web Content Rendering Engine
rc  libkidletime4                             4:4.8.5-0ubuntu0.1                      library to provide information about idle time
rc  libkio5                                   4:4.8.5-0ubuntu0.1                      Network-enabled File Management Library for the KDE Platform
rc  libkjsapi4                                4:4.8.5-0ubuntu0.1                      KJS API Library for the KDE Development Platform
rc  libkjsembed4                              4:4.8.5-0ubuntu0.1                      library for binding JavaScript objects to QObjects
rc  libkmediaplayer4                          4:4.8.5-0ubuntu0.1                      KMediaPlayer Interface for the KDE Platform
rc  libknewstuff2-4                           4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v2 Library for the KDE Platform
rc  libknewstuff3-4                           4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v3 Library for the KDE Platform
rc  libknotifyconfig4                         4:4.8.5-0ubuntu0.1                      library for configuring KDE Notifications
rc  libkntlm4                                 4:4.8.5-0ubuntu0.1                      NTLM Authentication Library for the KDE Platform
rc  libkparts4                                4:4.8.5-0ubuntu0.1                      Framework for the KDE Platform Graphical Components
rc  libkpty4                                  4:4.8.5-0ubuntu0.1                      Pseudo Terminal Library for the KDE Platform
rc  libkrosscore4                             4:4.8.5-0ubuntu0.1                      Kross Core Library
rc  libktexteditor4                           4:4.8.5-0ubuntu0.1                      KTextEditor interfaces for the KDE Platform
rc  libllvm3.1                                3.1-2ubuntu1~12.04                      Low-Level Virtual Machine (LLVM), runtime library
rc  libnepomuk4                               4:4.8.5-0ubuntu0.1                      Nepomuk Meta Data Library
rc  libnepomukdatamanagement4                 4:4.8.5-0ubuntu0.1                      Basic Nepomuk data manipulation interface
rc  libnepomukquery4a                         4:4.8.5-0ubuntu0.1                      Nepomuk Query Library for the KDE Platform
rc  libnepomuksync4                           4:4.8.5-0ubuntu0.1                      Nepomuk sync interface for the Backup and Sync service
rc  libnepomukutils4                          4:4.8.5-0ubuntu0.1                      Nepomuk Utility Library
rc  libntrack-qt4-1                           016-1ubuntu1                            Qt 4 API for ntrack
rc  libntrack0                                016-1ubuntu1                            lightweight connectivity tracking library
rc  libopenjpeg2                              1.3+dfsg-4+squeeze1build0.12.04.1       JPEG 2000 image compression/decompression library
rc  libphonon4                                4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - core library
rc  libplasma3                                4:4.8.5-0ubuntu0.1                      Plasma Library for the KDE Platform
rc  libpolkit-qt-1-1                          0.103.0-1                               PolicyKit-qt-1 library
rc  libprotoc7                                2.4.1-1ubuntu2                          protocol buffers compiler library
rc  libqapt-runtime                           1.3.1-0ubuntu2                          Runtime components for the QApt library
rc  libqapt1                                  1.3.1-0ubuntu2                          QApt library package
rc  libqca2                                   2.0.3-2                                 libraries for the Qt Cryptographic Architecture
rc  libqt4-designer                           4:4.8.1-0ubuntu4.4                      Qt 4 designer module
rc  libqt4-qt3support                         4:4.8.1-0ubuntu4.4                      Qt 3 compatibility library for Qt 4
rc  libqtwebkit4                              2.2.1-1ubuntu4                          Web content engine library for Qt
rc  librsync1                                 0.9.7-8build1                           rsync remote-delta algorithm library
rc  libsolid4                                 4:4.8.5-0ubuntu0.1                      Solid Library for KDE Platform
rc  libsoprano4                               2.7.5+dfsg.1-0ubuntu1                   libraries for the Soprano RDF framework
rc  libstreamanalyzer0                        0.7.7-1.1ubuntu3                        streamanalyzer library for Strigi Desktop Search
rc  libstreams0                               0.7.7-1.1ubuntu3                        streams library for for Strigi Desktop Search
rc  libsyncdaemon-1.0-1                       3.0.2-0ubuntu1                          Ubuntu One synchronization daemon library
rc  libthreadweaver4                          4:4.8.5-0ubuntu0.1                      ThreadWeaver Library for the KDE Platform
rc  libubuntuoneui-3.0-1                      3.0.1-0ubuntu1                          Ubuntu One widget library
rc  libvirtodbc0                              6.1.4+dfsg1-0ubuntu1                    high-performance database - ODBC libraries
rc  libxatracker1-lts-quantal                 9.0-0ubuntu1~precise4                   X acceleration library -- runtime
rc  libxrandr-ltsq2                           2:1.4.0-1~precise1                      X11 RandR extension library
rc  linux-image-3.5.0-23-generic              3.5.0-23.35~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  ntrack-module-libnl-0                     016-1ubuntu1                            libnl based ntrack module
rc  odbcinst                                  2.2.14p2-5ubuntu3                       Helper program for accessing odbc ini files
rc  odbcinst1debian2                          2.2.14p2-5ubuntu3                       Support library for accessing odbc ini files
rc  oxygen-icon-theme                         4:4.8.3-0ubuntu0.1                      Oxygen icon theme
rc  phonon                                    4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - metapackage
rc  popularity-contest                        1.53ubuntu1                             Vote for your favourite packages automatically
rc  python-ubuntuone-client                   3.0.2-0ubuntu1                          Ubuntu One client Python libraries
rc  python-ubuntuone-storageprotocol          3.0.2-0ubuntu1                          Python library for Ubuntu One file storage and sharing service
rc  sgml-data                                 2.0.6                                   common SGML and XML data
rc  ubuntuone-client                          3.0.2-0ubuntu1                          Ubuntu One client
rc  virtualbox                                4.1.12-dfsg-2ubuntu0.2                  x86 virtualization solution - base binaries
rc  virtualbox-qt                             4.1.12-dfsg-2ubuntu0.2                  x86 virtualization solution - Qt based user interface
rc  x11-xserver-utils-lts-quantal             7.7~3ubuntu1~precise1                   X server utilities
rc  xserver-common-lts-quantal                2:1.13.0-0ubuntu6.1~precise2            common files used by various X servers
rc  xserver-xorg-core-lts-quantal             2:1.13.0-0ubuntu6.1~precise2            Xorg X server - core server
rc  xserver-xorg-lts-quantal                  1:7.7+1ubuntu4~precise1                 X.Org X server
rc  xserver-xorg-video-intel-lts-quantal      2:2.20.9-0ubuntu2~precise2              X.Org X server -- Intel i8xx, i9xx display driver
rc  xserver-xorg-video-openchrome-lts-quantal 1:0.3.1-0ubuntu1~precise2               X.Org X server -- VIA display driver
rc  xserver-xorg-video-vmware-lts-quantal     1:12.0.2+git.e5ac80d8-0ubuntu1~precise2 X.Org X server -- VMware display driver

```

Should I still purge?

---

### Post by Bashing-om on 2013-04-18
fridgecow;

That list is much longer than I had expected. But as the status on all of them are "rc" I see no reason to "purge" anything at this point. We still do not know what is violating memory, Much less how.

Is your desk top mixed between kubuntu and ubuntu ? 
And, Let's get a clearer picture of your sources to see if there are any abnormalities.
```
apt-cache policy ubuntu-desktop
lsb_release -a
uname -a
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
```
More study on this situation is required on my part.[INDENT]
I am look'n, think'n and learn'n 
[/INDENT]

---

### Post by fridgecow on 2013-04-18
My desktop is Openbox, but I had kate installed which required the kde libraries. Anyway here's the result of those commands:
```
 root@isToms-PC:/home/istom# apt-cache policy ubuntu-desktopubuntu-desktop:
  Installed: 1.267.1
  Candidate: 1.267.1
  Version table:
 *** 1.267.1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1.267 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
root@isToms-PC:/home/istom# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise
root@isToms-PC:/home/istom# uname -a
Linux isToms-PC 3.5.0-26-generic #42~precise1-Ubuntu SMP Mon Mar 11 22:19:42 UTC 2013 i686 i686 i386 GNU/Linux
root@isToms-PC:/home/istom# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://www.remastersys.com/ubuntu precise main
root@isToms-PC:/home/istom# ls -la /etc/apt/sources.list.d
total 24
drwxr-xr-x 2 root root 4096 Apr  2 17:43 .
drwxr-xr-x 6 root root 4096 Apr  2 17:42 ..
-rw-r--r-- 1 root root  150 Apr  1 15:06 simonschneegans-testing-precise.list
-rw-r--r-- 1 root root  112 Apr  1 15:06 steam.list
-rw-r--r-- 1 root root  112 Apr  1 15:06 steam.list.save
-rw-r--r-- 1 root root   39 Apr  2 17:43 winswitch.list

```

---

### Post by Bashing-om on 2013-04-18
fridgecow;
Here are my thoughts:
Everything looks good but I find the 3rd party software as the most likely cause at this point;
Try this:
Disable (uncheck) all the 3rd party sources in ubuntu Software Center ->Software Sources and run
```
sudo apt-get update
sudo apt-get upgrade
``` again. Let us see what errors we then have.

But, I still intend to do some home work.[INDENT=2]
a process in learning

[/INDENT]

---

### Post by Bashing-om on 2013-04-18
fridgecow;

Are you ready to proceed ? I have been look'n and study'n.
The dpkg list with all those files marked "rc" ; let's get rid of them.
The state is "rc", the package is removed, but the config files are not removed.
Now let’s remove all the packages marked as "rc".
```
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```[INDENT=2]
now what are you looking like 

[/INDENT]

---

### Post by fridgecow on 2013-04-19
When I try it, nothing happens. Nothing is removed either.
> 
istom@isToms-PC:~$ sudo dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
istom@isToms-PC:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
istom@isToms-PC:~$ 

---

### Post by Bashing-om on 2013-04-19
What does :
```
sudo dpkg -l | grep -v ^ii 
``` now return ?
And are the 3rd party sources disabled at this time ?[INDENT=2]
work'n on it

[/INDENT]

---

