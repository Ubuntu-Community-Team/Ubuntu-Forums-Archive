---
title: "acetoneISO, install troubles"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by itachis.eyes on 2009-11-25
for starters they debian package they hosted is no longer there for download
so i just got the source code and rather then ./configure they have this "qmake-qt4" and i installed it and kinda poked around and guessed as to the command arguments (it wouldn't work without them) and now i get to the make command and i get this error message:
```
/usr/bin/uic-qt4 acetoneiso/ui/about.ui -o ui_about.h
make: /usr/bin/uic-qt4: command not found
make: *** [ui_about.h] error 127
```i'm not sure where to go from here (and yes i am running the terminal as superuser) but i need to get this program (or at least a simular program) installed. what it is, is a universal image program that can open/mount dmg img iso and a bunch of other image files (those are the big three that i'm worried about) 

thanks for any help given, and if you need more information please do ask and i'll post as soon as i read the post

---

### Post by BenAshton24 on 2009-11-25
```
sudo apt-get install libqt4-dev
```

---

### Post by itachis.eyes on 2009-11-25
> **BenAshton24 said:**
> ```
sudo apt-get install libqt4-dev
```

THANKS! 
*face palm* i'm not used to checking dependencies yet....*sobs at lack of linux experience*

---

### Post by bulletxt on 2009-11-29
1: there is an official ubuntu package, just go on the official website [www.acetoneteam.org](www.acetoneteam.org)

2: you just had to read the README in the source package that clearly states you need libqt4-dev

:)

---

### Post by zzzisgood on 2010-05-02
[http://www.acetoneteam.org/](http://www.acetoneteam.org/) says "Ubuntu: starting from Ubuntu 10.04 and up "apt-get install acetoneiso", or here", however, acetoneiso is not in repository of Ubuntu Karmic , Moreover, the alternative getdeb does not work for me somehow, I therefore have to download the source, but failed 
with following errors , 

sudo apt-get install fuseiso fuse-utils libqt4-gui genisoimage cdrdao p7zip-full gnupg-agent gnupg2 pinentry-qt4 ffmpeg mencoder cdparanoia

sudo apt-get install phonon libphonon-dev libphonon4 phonon-backend-gstreamer

make
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DQT_NO_DEBUG -DQT_WEBKIT_LIB -DQT_PHONON_LIB -DQT_DBUS_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtDBus -I/usr/include/phonon -I/usr/include/qt4/QtWebKit -I/usr/include/qt4 -I. -Ibuild -Ibuild -o build/acetoneiso.o sources/acetoneiso.cpp
In file included from sources/acetoneiso.cpp:60:
sources/erase_cd.h:21:30: error: Phonon/MediaObject: No such file or directory
sources/erase_cd.h:22:30: error: Phonon/AudioOutput: No such file or directory
In file included from sources/acetoneiso.cpp:53:
sources/utube.h: In member function ‘void acetoneiso::utube()’:
sources/utube.h:25: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
sources/utube.h: In member function ‘void acetoneiso::utubeuser()’:
sources/utube.h:71: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
sources/utube.h: In member function ‘void acetoneiso::metacafe()’:
sources/utube.h:129: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
make: *** [build/acetoneiso.o] Error 1
wang@ds-server:~/downloads/acetoneiso_2.2.1/acetoneiso$ 

can anyone points out what's wrong here?

---

