---
title: "Problem with autoconf macro"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by thotmos on 2008-05-19
Hi there!
I was writing a small project in using Qt toolkit
and I was trying autotools for standardization 
and used the macro BNV_HAVE_QT from autoconf_archive.
Now I run aclocal, autoconf, automake -a
the configure script is ready but it shows the following
```
sameh@desktop:~/dev/datastrqt/dateqt$ export PATH=/usr/share/qt4/bin:$PATH
sameh@desktop:~/dev/datastrqt/dateqt$ ./configure --prefix=/usr --with-Qt-include-dir=/usr/include/qt4
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
...
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for Qt... yes:
    QT_CXXFLAGS=-I/usr/include/qt4 -DQT_THREAD_SUPPORT
    QT_DIR=
    QT_LIBS=-L/usr/lib -lqt-mt  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi
    QT_UIC=/usr/share/qt4/bin/uic
    QT_MOC=/usr/share/qt4/bin/moc
    QT_LRELEASE=/usr/share/qt4/bin/lrelease
    QT_LUPDATE=/usr/share/qt4/bin/lupdate
checking correct functioning of Qt installation... failure
configure: error: Failed to find matching components of a complete
                  Qt installation. Try using more options,
                  see ./configure --help.

```
for some reason the script does not find qt4, why

---

### Post by thotmos on 2008-05-19
don't bother, i think i solved it
> 
```

checking for Qt... yes:
..
    QT_LIBS=-L/usr/lib -lqt-mt  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi
..
checking correct functioning of Qt installation... failure

```

the script finds Qt but because the macro points to 
qt-mt (which belongs to Qt3) it can't find a functioning 
installation. I used the configure.ac and Makefile.am from a nice app called qcomicbook
[http://www.kde-apps.org/content/show.php?content=19509]("http://www.kde-apps.org/content/show.php?content=19509") and it actually worked,  
thanks Pawel!

---

