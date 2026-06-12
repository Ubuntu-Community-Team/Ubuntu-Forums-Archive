---
title: "Help needed for compiling RLPlot"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by sureinlux on 2007-02-12
Hi there,
 Am a newbie, and I wanted to compile the latest [RLPlot]("http://rlplot.sourceforge.net/") (a WYSIWYG scientific plotting tool), since the one in the repo is an older version. It is a qt3 application. I downloaded the [source code]("http://jaist.dl.sourceforge.net/sourceforge/rlplot/rlplot_1.2.tar.gz"), and read the README, which was a but confusing. Any help in compiling the application will be great...

I installed [FONT="Courier New"]qt3-dev-tools[/FONT] and located [FONT="Courier New"]qapplication.h[/FONT] in /usr/include/qt3
also it searches for moc, it is in /usr/bin/moc and also (confusingly) qt3-moc is also there. 

After i edited the Makefile for the QTDIR from /usr/lib/qt3 to /usr/include/qt3, I said make -e
and this was the error message:

```
make rlplot QTDIR=/usr/include/qt3 
make[1]: Entering directory `/home/me/rlplot'
/usr/include/qt3/bin/moc ./QT_Spec.h -o moc_QT_Spec.cpp
make[1]: /usr/include/qt3/bin/moc: Command not found
make[1]: *** [moc_QT_Spec.cpp] Error 127
make[1]: Leaving directory `/home/me/rlplot'
make: *** [all] Error 2
```

---

