---
title: "Installing Stellarium 0.10.0 from source"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by status001 on 2008-10-03
[FONT="Book Antiqua"][SIZE="3"]I've been using Ubuntu Hardy for eight month. That makes me a newbie to this. I figured out the most difficult thing about Linux is installing a software without any internet connection. Even if you have a net connection, you may have not the updated version of a software since it is not added to your repository. I use Stellarium-the desktop planetrium of version 0.9.1. Wherever, I've found out that, later two versions are already released. I've download the source file from here

[[COLOR="Blue"]http://www.stellarium.org/[/COLOR]]("http://www.stellarium.org/")
[[COLOR="SeaGreen"]http://downloads.sourceforge.net/stellarium/stellarium-0.10.0.tgz[/COLOR]]("http://downloads.sourceforge.net/stellarium/stellarium-0.10.0.tgz")

I found too many ways to install this source in internet, but since I'm a newbie, I don't know what to do exactly. If you are kind enough, please download and install it yourself and post the whole process on this thread. I'll be very pleased for this help. Thanks in advance.[/SIZE][/FONT]

**Please do not post any link that leads me to another page. If you are very interested, then do what I'm asking. Thanks.**

---

### Post by status001 on 2008-10-04
anyone???

---

### Post by Partyboi2 on 2008-10-04
First open a terminal (Applications>Accessories>Terminal) then install a few packages that you will need installed to compile this program.
```
sudo apt-get install build-essential automake1.9  autoconf cmake gettext libgl1-mesa-dev libglu1-mesa-dev  libsdl-dev  zlib1g-dev  libpng12-dev libfreetype6-dev libboost-dev libjpeg62-dev  libcurl3-dev  libqt4-dev doxygen  graphviz libsdl-mixer1.2-dev 
```
Then download the Sterllarium program if you have not already done so to your Desktop. Then change directory to your Desktop
```
cd ~/Desktop
``` then extract the downloaded file with
```
tar zxf stellarium-0.10.0.tar.gz
``` then change into the newly made directory
```
cd stellarium-0.10.0
``` then make a directory that you are going to use to build it
```
mkdir -p builds/unix
``` Then change into the newly made builds directory
```
cd builds/unix
```
then```
cmake
```
If that passes without errors then move onto make
```
make
``` if that passes without errors install it with
```
sudo make install
```
If you don't want to install it but just want to run it, you can do that by skipping the sudo make install part and doing this:
```
cd ../..
```
```
builds/unix/src/stellarium
```

---

### Post by status001 on 2008-10-07
***@Partyboi2***
If you really want to help then please download it compile and install and post the terminal log. Please do not just copy paste some command from another web page. I've read this instruction before I post this thread here. Atleast you can help me by downloading any small package source compile and install it on your computer and please post your terminal log here. That will be very generous of you. Thanks.

---

### Post by Partyboi2 on 2008-10-07
> 
If you really want to help then please download it compile and install and post the terminal log. 
I did download and compile this program. You just did not mention in your first post that you were wanting terminal logs :)

> Please do not just copy paste some command from another web page.
What I posted was the steps I took to compile this program. All you have to do is copy and paste them into a terminal. :)

>  Atleast you can help me by downloading any small package source compile and install it on your computer and please post your terminal log here. That will be very generous of you. Thanks. I have since reinstalled ubuntu, but if I have time tomorrow I will download and compile it again and uploaded my terminal logs for you. :)

---

### Post by Partyboi2 on 2008-10-07
Here are the terminal logs.

---

### Post by status001 on 2008-10-09
*Thanks for the log. But, still not working. I don't know what is my problem. Everything goes right till 13% of installation. Here is my log. If you do understad this promlem, please help. And by the way, are you using Intrepid? Mine is hardy. Is there anything problem with that. I've installed all the dependecies mentioned in Stellarium-Wiki.*

```
ediamin@ediamin-desktop:~/Desktop/stellarium-0.10.0/builds/unix$ make
[  0%] Generating ui_locationDialogGui.h
[  0%] Generating ui_helpDialogGui.h
[  0%] Generating ui_dateTimeDialogGui.h
[  0%] Generating ui_viewDialog.h
[  0%] Generating ui_searchDialogGui.h
[  0%] Generating ui_configurationDialog.h
[  2%] Built target GenerateUiHeaders
[  2%] Generating qrc_mainRes.cxx
[  2%] Generating moc_StelModuleMgr.cxx
[  2%] Generating moc_Observer.cxx
[  3%] Generating moc_StelApp.cxx
[  3%] Generating moc_Navigator.cxx
[  3%] Generating moc_LocationMgr.cxx
[  4%] Generating moc_Projector.cxx
[  4%] Generating moc_StelAppGraphicsScene.cxx
[  4%] Generating moc_STexture.cxx
[  5%] Generating moc_MovementMgr.cxx
[  5%] Generating moc_SkyImageTile.cxx
[  5%] Generating moc_SkyDrawer.cxx
[  6%] Generating moc_ConstellationMgr.cxx
[  6%] Generating moc_LandscapeMgr.cxx
[  6%] Generating moc_GridLinesMgr.cxx
[  6%] Generating moc_MilkyWay.cxx
[  7%] Generating moc_NebulaMgr.cxx
[  7%] Generating moc_SkyBackground.cxx
[  7%] Generating moc_SolarSystem.cxx
[  8%] Generating moc_MeteorMgr.cxx
[  8%] Generating moc_StarMgr.cxx
[  8%] Generating moc_StelGui.cxx
[  9%] Generating moc_StelGuiItems.cxx
[  9%] Generating moc_HelpDialog.cxx
[  9%] Generating moc_Dialog.cxx
[ 10%] Generating moc_MapLabel.cxx
[ 10%] Generating moc_AngleSpinBox.cxx
[ 10%] Generating moc_LocationDialog.cxx
[ 11%] Generating moc_DateTimeDialog.cxx
[ 11%] Generating moc_ViewDialog.cxx
[ 11%] Generating moc_SearchDialog.cxx
[ 11%] Generating moc_ConfigurationDialog.cxx
[ 12%] Generating moc_StelDialog.cxx
[ 12%] Generating moc_StelMainGraphicsView.cxx
[ 12%] Generating moc_StelMainWindow.cxx
[ 13%] Generating moc_QtScriptMgr.cxx
Scanning dependencies of target stellarium
[ 13%] Building CXX object src/CMakeFiles/stellarium.dir/core/Audio.o
[ 13%] Building CXX object src/CMakeFiles/stellarium.dir/core/GeodesicGrid.o
[ 14%] Building CXX object src/CMakeFiles/stellarium.dir/core/LoadingBar.o
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp:28:21: error: QGLWidget: No such file or directory
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp: In member function &#8216;void LoadingBar::Draw(float)&#8217;:
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp:116: error: invalid use of incomplete type &#8216;struct QGLWidget&#8217;
/usr/include/qt4/QtGui/qpixmap.h:241: error: forward declaration of &#8216;struct QGLWidget&#8217;
make[2]: *** [src/CMakeFiles/stellarium.dir/core/LoadingBar.o] Error 1
make[1]: *** [src/CMakeFiles/stellarium.dir/all] Error 2
make: *** [all] Error 2
ediamin@ediamin-desktop:~/Desktop/stellarium-0.10.0/builds/unix$ sudo make
[sudo] password for ediamin: 
[  2%] Built target GenerateUiHeaders
[  3%] Building CXX object src/CMakeFiles/stellarium.dir/core/LoadingBar.o
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp:28:21: error: QGLWidget: No such file or directory
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp: In member function &#8216;void LoadingBar::Draw(float)&#8217;:
/home/ediamin/Desktop/stellarium-0.10.0/src/core/LoadingBar.cpp:116: error: invalid use of incomplete type &#8216;struct QGLWidget&#8217;
/usr/include/qt4/QtGui/qpixmap.h:241: error: forward declaration of &#8216;struct QGLWidget&#8217;
make[2]: *** [src/CMakeFiles/stellarium.dir/core/LoadingBar.o] Error 1
make[1]: *** [src/CMakeFiles/stellarium.dir/all] Error 2
make: *** [all] Error 2
ediamin@ediamin-desktop:~/Desktop/stellarium-0.10.0/builds/unix$ cd ..
```

---

### Post by torpe0 on 2008-10-09
> **status001 said:**
> *Thanks for the log. But, still not working. I don't know what is my problem. Everything goes right till 13% of installation. Here is my log. If you do understad this promlem, please help. And by the way, are you using Intrepid? Mine is hardy. Is there anything problem with that. I've installed all the dependecies mentioned in Stellarium-Wiki.*



Are you sure? From the error it looks like you are missing libqt4-dev. Copy the code below and paste it into terminal (thats ctrl+shift+v), then try again.

--
Tor Arne Pedersen
[http://hitthebutton.org]("http://hitthebutton.org")

```

sudp aptitude install build-essential libfreetype6-dev cvs libsdl-mixer1.2-dev \
     libpng12-dev libsdl1.2-dev zlib1g-dev libglu1-mesa-dev libgl1-mesa-dev gcc \
     g++ gettext libboost-dev libboost-thread-dev libjpeg-dev \
     libboost-filesystem-dev subversion libqt4-dev graphviz doxygen cmake

```

---

### Post by status001 on 2008-10-10
> **torpe0 said:**
> Are you sure? From the error it looks like you are missing libqt4-dev. Copy the code below and paste it into terminal (thats ctrl+shift+v), then try again.

```

sudp aptitude install build-essential libfreetype6-dev cvs libsdl-mixer1.2-dev \
     libpng12-dev libsdl1.2-dev zlib1g-dev libglu1-mesa-dev libgl1-mesa-dev gcc \
     g++ gettext libboost-dev libboost-thread-dev libjpeg-dev \
     libboost-filesystem-dev subversion libqt4-dev graphviz doxygen cmake

```

[FONT="Trebuchet MS"][SIZE="2"]I've seen this list before. And I download all these dependencies. 
One thing you don't know that, this version of 
Stellarium needs libqt4-dev version >=4.4.1. 
Which is not in Hardy repository yet. Though, 
I download libqt4-dev 4.4.3 from ubuntu launchpad.net and installed them. There were no dependency problem for it. Later, I check the above dependency list using Synaptic Package Manger. I can asure you, all the dependencies were installed in Synaptic. Now, any suggestion?[/SIZE][/FONT]

---

### Post by cvaty on 2008-10-15
any idea whats going on? 

sudo apt-get install  libqt4-dev
```
The following packages have unmet dependencies:
  libqt4-dev: Depends: libqt4-assistant (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-dbus (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqt4-designer (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-help (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-network (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-qt3support (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-script (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-sql (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-svg (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-test (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-webkit (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-xml (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqt4-xmlpatterns (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqtgui4 (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
E: Broken packages
```

~/Desktop/stellarium-0.10.0/builds/unix$ cmake ../..
```

u-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for include files HAVE_BYTESWAP_H
-- Looking for include files HAVE_BYTESWAP_H - found
-- Looking for tzset
-- Looking for tzset - found
-- Looking for pow10
-- Looking for pow10 - not found
-- Looking for setlocale
-- Looking for setlocale - found
-- Looking for snprintf
-- Looking for snprintf - found
CMake Error at cmake/FindQt4.cmake:1278 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:78 (FIND_PACKAGE)


```

---

### Post by Partyboi2 on 2008-10-15
> **cvaty said:**
> any idea whats going on? 

sudo apt-get install  libqt4-dev
```
The following packages have unmet dependencies:
  libqt4-dev: Depends: libqt4-assistant (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-dbus (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqt4-designer (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-help (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-network (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-qt3support (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-script (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-sql (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-svg (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-test (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-webkit (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqt4-xml (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqt4-xmlpatterns (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
              Depends: libqtcore4 (= 4.4.0-1ubuntu5~hardy1) but 4.4.3-0ubuntu1 is to be installed
              Depends: libqtgui4 (= 4.4.0-1ubuntu5~hardy1) but it is not going to be installed
E: Broken packages
```~/Desktop/stellarium-0.10.0/builds/unix$ cmake ../..
```

u-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for include files HAVE_BYTESWAP_H
-- Looking for include files HAVE_BYTESWAP_H - found
-- Looking for tzset
-- Looking for tzset - found
-- Looking for pow10
-- Looking for pow10 - not found
-- Looking for setlocale
-- Looking for setlocale - found
-- Looking for snprintf
-- Looking for snprintf - found
CMake Error at cmake/FindQt4.cmake:1278 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:78 (FIND_PACKAGE)


```
Have you got the repos enabled in Software Sources first tab?

---

### Post by forevry on 2008-10-25
1. add  in /etc/apt/sources.list

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main universe restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main universe restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main universe restricted multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main universe restricted multiverse


2. sudo apt-get update

3. sudo apt-get  install libqt4-dev libqt4-opengl-dev 

4. clean and repeat installation

5. (delete rows of intrepid rep  in /etc/apt/sources.list)

6. sudo apt-get update

---

### Post by forevry on 2008-10-25
1. add in /etc/apt/sources.list

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main universe restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main universe restricted multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main universe restricted multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) intrepid-updates main universe restricted multiverse


2. sudo apt-get update

3. sudo apt-get install libqt4-dev libqt4-opengl-dev

4. clean and repeat installation

5. (delete rows of intrepid rep in /etc/apt/sources.list)

6. sudo apt-get update
Last edited by forevry; 1 Minute Ago at 10:59 PM.

---

### Post by DarkDead on 2008-10-25
Hi.
forevry to use your solution I would have to do all this:
```
Packages to removed:
  libcupsys2 libgail-common libgail18 libgnomekbd2 libgnomekbdui2
New packages to be installed:
  cups cups-bsd cups-client cups-common cups-driver-gutenprint libcamel1.2-14
  libcanberra-gtk0 libcanberra0 libcups2 libedataserver1.2-11
  libgnome-desktop-2-7 libgnomekbd3 libgnomekbdui3 libgnutls26 libijs-0.35
  libilmbase6 libltdl7 libopenexr6 libpoppler3 libtalloc1 libwbclient0
  libxcb-render-util0 libxcb-render0 python-cupshelpers python-usb
  ubuntu-system-service
Packages to be updated:
  capplets-data cupsddk cupsddk-drivers cupsys cupsys-bsd cupsys-client
  cupsys-common cupsys-driver-gutenprint findutils gconf2 gconf2-common
  gnome-control-center gnome-screensaver gnome-settings-daemon
  gtk2-engines-pixbuf hal-cups-utils hpijs hplip hplip-data kdelibs4c2a
  libasound2 libc6 libc6-dev libc6-i686 libcairo2 libcupsimage2 libebook1.2-9
  libeel2-2 libgconf2-4 libgcrypt11 libglib2.0-0 libglib2.0-dev
  libgnome-window-settings1 libgnomecanvas2-0 libgnomecups1.0-1
  libgnomekbd-common libgnomeprint2.2-0 libgnomeprint2.2-data libgs8
  libgtk2.0-0 libgtkhtml2-0 libgtkhtml3.14-19 libgutenprint2 libpango1.0-0
  libpango1.0-common libpixman-1-0 libpolkit-dbus2 libpolkit2 libpopt0
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-dev libqt4-help
  libqt4-network libqt4-opengl libqt4-opengl-dev libqt4-qt3support
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libselinux1
  libsoup2.4-1 libsqlite3-0 libxi-dev libxi6 libxklavier12 lsb-base nautilus
  nautilus-data nautilus-share python-cups samba samba-common smbclient splix
  winbind x11proto-input-dev
```
Here are many important packages like cups. Is it safe to update them from this repos?

Is there any way to just get the libqt4-dev and libqt4-opengl-dev .deb files?

---

### Post by Partyboi2 on 2008-10-26
From my experiences installing packages from one version of ubuntu with another can end up with breakages. Stellarium is in the hardy repos so you should be able to install by terminal
```
sudo apt-get install stellarium
``` If you are wanting to compile the latest version from souce then make sure that you have the repos enable in Software Sources (System>Admin>Software Sources>1st Tab) then install the development packages by
```
sudo apt-get build-dep stellarium
```
Then compile it.

---

### Post by Shazaam on 2008-10-26
I had the same problem as the others- libqt4-dev is 4.3.4 in standard Hardy repo's. Enabling Hardy backports gets you 4.4.1 but Stellarium source requires 4.4.3 so I gave up and will install Hardy's repo version. :)

---

### Post by DarkDead on 2008-10-26
Hi agin.

@Partyboi2: Thanks for the help. When I try your command (with all the source code repos enabled) I don't get anything:
```
david@principal:~$ sudo apt-get build-dep stellarium
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Lendo informação de estado... Pronto
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
```
Any idea?

@status001: Which dependencies did you install in order to install libqt3-dev 4.4.3 from ubuntu launchpad.net?

---

### Post by AnotherFineMess on 2008-11-07
The package manager Ubuntu Linux uses (apt-get) is an excellent tool though it can get caught back on providing the latest versions. It is not reasonable expecting a Linux user who wants to use a piece of software to have all his dependencies correct, and follow a page of instruction on compiling Stellarium from source. I really hate this fragmentation on how software is installed under linux (bin's, deb's, rmp's, tar's, run's) you name it. Linux needs a universal way of installing any of the above package formats.
As for stellarium i love this piece of software, because i cant afford yet to buy a good telescope, only a cheap eee pc, running the most loved and well supported distro here today: Ubuntu. I had no luck on compiling the 0.10.0 version, and i hate the fact that i'll have to wait another six months to get the latest version on the official repos. Stellarium ought to start working with repositories soon enough, because thats what all the cool open source vendors are doing. 
Getdeb is a good attempt in order to provide latest packages though it as well was caught behind with the amount of software titles

---

