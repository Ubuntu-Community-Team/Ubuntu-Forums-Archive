---
title: "Vidalia does not compile with QT4 under Dapper"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by sageb1 on 2008-02-16
This is a heads up that vidalia does not compile using the dapper qt4 library which is version 4.1.2.

When I got this error:

> 
$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT  -DQT_NO_DEBUG -DQT_XML_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4 -Isrc/gui/common -Isrc/gui/help/browser -Isrc/lang -Isrc -Isrc/config -Isrc/control -Isrc/gen/moc -Isrc/gen/ui -o obj/mainwindow.o src/gui/mainwindow.cpp
src/gen/ui/ui_serverpage.h: In member function &#8216;void Ui_ServerPage::setupUi(QWidget*)&#8217;:
src/gen/ui/ui_serverpage.h:537: error: &#8216;class QLabel&#8217; has no member named &#8216;setTextInteractionFlags&#8217;
src/gen/ui/ui_serverpage.h:537: error: &#8216;TextSelectableByMouse&#8217; is not a member of &#8216;Qt&#8217;
src/gen/ui/ui_serverpage.h:550: error: &#8216;class QLabel&#8217; has no member named &#8216;setTextInteractionFlags&#8217;
src/gen/ui/ui_serverpage.h:550: error: &#8216;TextSelectableByMouse&#8217; is not a member of &#8216;Qt&#8217;
make: *** [obj/mainwindow.o] Error 1


I realized after much research that QLabel and TextSelectablebyMouse need at the least version 4.2 not 4.1 as stated in the text:

[http://trac.vidalia-project.net/wiki/InstallSource?format=txt](http://trac.vidalia-project.net/wiki/InstallSource?format=txt)

> 
  1. Make sure you have [[http://www.trolltech.com/download/opensource.html](http://www.trolltech.com/download/opensource.html) Qt 4.1 or later] and [[https://www.torproject.org/download.html](https://www.torproject.org/download.html) Tor 0.1.2.x or later] installed.


This implies that vidalia will not work for 6.06 LTS.

---

