---
title: "QTDIR not found / Howto set environment variable?"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by lenn-art on 2007-11-15
I'm trying to compile a program. When i run ./configure, i get the error > configure: error: QTDIR environment variable must be set
Strangely enough, if i give the commando > $ $QTDIR i get the output > bash: /usr/share/qt4: is a folderSo, i think the QTDIR is set, but why can't he be found by ./configure?

---

### Post by tschenk on 2007-11-15
Maybe the application you would like to compile is based on the qt3
and not the qt4 libraries.
I found this two hints once:

This worked for me on Xubuntu 6.06:
If you have to use the qt3-libs, 
type:
> sudo ln -s -f /usr/bin/qmake-qt3 /usr/bin/qmake 
and:
>  export QTDIR=/usr/share/qt3 
(source: [http://ubuntufromscratch.wordpress.com/problemes-de-compilations-qt3-et-qt4/](http://ubuntufromscratch.wordpress.com/problemes-de-compilations-qt3-et-qt4/))

If it still doesn't work (or it is not an qt3-program)
you might have to do other modifications:
(this worked for me once on OSX10.3)

> export QTDIR=/usr/share/qt3
(or: > export QTDIR=/usr/share/qt4 )
> export PATH=$QTDIR/bin:$PATH
> export LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH
(source: [http://www.linuxforen.de/forums/showthread.php?t=105210](http://www.linuxforen.de/forums/showthread.php?t=105210))

Hope it helps

---

