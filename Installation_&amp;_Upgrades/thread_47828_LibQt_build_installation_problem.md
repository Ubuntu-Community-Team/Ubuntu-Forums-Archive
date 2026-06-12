---
title: "LibQt build installation problem"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by pt123 on 2005-07-10
I am trying to build this program Moviefly [https://savannah.nongnu.org/projects/lmc/](https://savannah.nongnu.org/projects/lmc/)

When I type ./configure 

I am getting this  error.
```
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for Qt... ls: /lib/libqt*: No such file or directory
/usr/lib/libqt-mt.so.3      /usr/lib/libqt.so.3.3.3
/usr/lib/libqt-mt.so.3.3    /usr/lib/libqthreads.so.12
/usr/lib/libqt-mt.so.3.3.3  /usr/lib/libqthreads.so.12.3.0
/usr/lib/libqt.so.3         /usr/lib/libqtmcop.so.1
/usr/lib/libqt.so.3.3       /usr/lib/libqtmcop.so.1.0.0
yes:
    QT_CXXFLAGS=-I/usr/include/qt3
    QT_DIR=
    QT_LIBS=-l/usr/lib -l   -lX11 -lXext -lXmu -lXt -lXi
    QT_UIC=
    QT_MOC=
checking correct functioning of Qt installation... failure
configure: error: Failed to find matching components of a complete
                  Qt installation. Try using more options,
                  see ./configure --help.
``` 

BUt I have libqt-mt 3.3 installed its says in Synaptic,
 can someone guide me as to what I am doing wrong?

---

### Post by llamakc on 2005-07-10
In Debian-based distributions one must usually install the -dev package to compile other software against.

```

[ken:init.d](06:56 AM)$ apt-cache search libqt-mt
libqt3-dev - Qt development files
libqt3-headers - Qt3 header files
libqt3-mt-dev - Qt development files (Threaded)
libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3

```

I would install libqt3-mt-dev and give that ./configure another whirl. Rinse, repeat.

---

### Post by pt123 on 2005-07-11
[QUOTE=llamakc]In Debian-based distributions one must usually install the -dev package to compile other software against.

I would install libqt3-mt-dev and give that ./configure another whirl. Rinse, repeat.[/QUOTE]

I had that installed, I think it has more to do with the PKG_CONFIG_PATH & set LIBRARY_PATH.

As the files are in lib folders but  for some reason it can't find it.


But this forum has hardly anything on PKG_CONFIG_PATH, most threads on this have been left unanswered.  ](*,)  ](*,)

---

### Post by longinus on 2006-06-17
Sorry to ressurect and old topic, but I can't compile Moviefly also.. The same error.. And I have installed all the qt3 packages I found..  I also tried using the deb for Moviefly, but it need some dependencies that conflict with ubuntu ones..

So for anyone interested in using the program, the original, windows version, Ant Movie Catalog works fine under wine.

---

### Post by wadubois on 2006-07-19
WHile I was attempting to compile Rosegarden tonight, I might have stumbled upon your answer.  I found a second qt3 directory installed under /usr/share.

THis worked for me (Rosegarden also uses scons):
scons qtdir=/usr/share/qt3.

Perhaps this will work also for your .configure problem if you declare: export QTDIR=/usr/share/qt3;./configure

Good luck.

 - w

---

### Post by megamaced on 2006-08-05
wadubois, please PLEASE tell me how you compiled Rosegarden!!

I issued the command 'scons qtdir=/usr/share/qt3' but then it asked me for my KDE includes directory!

I am stuck!

---

### Post by burningbunny on 2006-09-17
Anyone found a solution for this yet?
Just tried to compile Moviefly and this is the only thread that addresses the error I have...

---

### Post by pt123 on 2006-09-17
Just use Wine and AMC it works flawlessly in it.

---

### Post by nicoladimaria on 2007-04-15
> **wadubois said:**
> Perhaps this will work also for your .configure problem if you declare: export QTDIR=/usr/share/qt3;./configure
no, it does not work
thanks anyway

---

