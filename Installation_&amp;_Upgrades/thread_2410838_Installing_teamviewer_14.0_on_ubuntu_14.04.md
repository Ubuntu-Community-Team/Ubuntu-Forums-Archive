---
title: "Installing teamviewer 14.0 on ubuntu 14.04"
date: 2019-01-21
forum: Installation &amp; Upgrades
---

### Post by natenbaptista on 2019-01-21
Iam trying to install Teamviewer 14.0.14470 or teamviewer_14.0.14470_amd64.deb to be precise.
I have tried using the software center but the gui shows "**Dependency is not satisfiable: libqt5gui | qt56-teamviewer**".
Tried to install using "**sudo dpkg -i teamviewer_14.0.14470_amd64.deb**" but get a series of dependency problems like so ...

```
 ...
teamviewer depends on libqt5gui5 (>= 5.5) | qt56-teamviewer; however:
  Version of libqt5gui5:amd64 on system is 5.2.1+dfsg-1ubuntu14.3.
  Package qt56-teamviewer is not installed.
 teamviewer depends on libqt5widgets5 (>= 5.5) | qt56-teamviewer; however:
  Version of libqt5widgets5:amd64 on system is 5.2.1+dfsg-1ubuntu14.3.
  Package qt56-teamviewer is not installed
... 
```

Checked version of qt using 

```
atp@atp-2404:~/Downloads$ qmake --version
QMake version 3.0
Using Qt version 5.2.1 in /usr/lib/x86_64-linux-gnu
atp@atp-2404:~/Downloads$ 

```

Shows qt 5.2 is installed.
Tried to install libqt5gui5

```
atp@atp-2404:~/Downloads$ sudo apt-get install libqt5gui5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5gui5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Shows that libqt5gui5 is already there.
But then qtchooser shows this

```
atp@atp-2404:~/Downloads$ qtchooser -list-versions
4
5
default
qt4-i386-linux-gnu
qt4-x86_64-linux-gnu
qt4
qt5-x86_64-linux-gnu
qt5

```

Seems there are two versions of Qt and installing libqt5gui5 says its already at the newer version but then the Teamviewer install still fails.
Anyone had this problem?

---

### Post by howefield on 2019-01-21
Try the newest release [14.1.3399]("https://www.teamviewer.com/en/download/linux/")

---

### Post by Impavidus on 2019-01-21
Welcome to dependency hell.

Your package needs a version of a library that's not available from the repositories of Ubuntu 14.04. On Ubuntu 14.04, libqt5gui5 was frozen at version 5.2 and you need at least 5.5. I should also remind you that Ubuntu 14.04 only has about 3 months of support left, so it's time to move to a more recent release, either 16.04 LTS or jump straight to 18.04 LTS. Both Ubuntu releases come with a version of libqt5gui5 that satisfies your dependency (5.5 and 5.9).

---

