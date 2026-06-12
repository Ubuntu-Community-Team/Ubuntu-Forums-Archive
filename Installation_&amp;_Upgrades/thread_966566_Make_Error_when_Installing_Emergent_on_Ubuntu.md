---
title: "Make Error when Installing Emergent on Ubuntu"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by excetara2 on 2008-11-01
I am trying to install Emergent Neural Networking Software on Ubuntu 8.04.

I have followed primarily the directions on this page and installed all the pre-requisites.

[http://grey.colorado.edu/emergent/index.php/Build_(Linux](http://grey.colorado.edu/emergent/index.php/Build_(Linux))

I get an error during the make of emergent. Any help would be appreciated to what the error means. I will paste the code below. Put a couple commands before the error in here to:

ar cru .libs/libtaiqtso_4.0.18.a .libs/libtaiqtso_4.0.18_la-iflowlayout.o .libs/libtaiqtso_4.0.18_la-iformlayout.o .libs/libtaiqtso_4.0.18_la-ilabel.o .libs/libtaiqtso_4.0.18_la-ilabel.moc.o .libs/libtaiqtso_4.0.18_la-icliptoolwidget.o .libs/libtaiqtso_4.0.18_la-icliptoolwidget.moc.o .libs/libtaiqtso_4.0.18_la-ispinbox.o .libs/libtaiqtso_4.0.18_la-ispinbox.moc.o .libs/libtaiqtso_4.0.18_la-itreewidget.o .libs/libtaiqtso_4.0.18_la-itreewidget.moc.o .libs/libtaiqtso_4.0.18_la-ilineedit.o .libs/libtaiqtso_4.0.18_la-ilineedit.moc.o .libs/libtaiqtso_4.0.18_la-idialog.o .libs/libtaiqtso_4.0.18_la-idialog.moc.o .libs/libtaiqtso_4.0.18_la-icheckbox.o .libs/libtaiqtso_4.0.18_la-icheckbox.moc.o .libs/libtaiqtso_4.0.18_la-icombobox.o .libs/libtaiqtso_4.0.18_la-icombobox.moc.o .libs/libtaiqtso_4.0.18_la-igeometry.o .libs/libtaiqtso_4.0.18_la-ieditgrid.o .libs/libtaiqtso_4.0.18_la-ieditgrid.moc.o .libs/libtaiqtso_4.0.18_la-idimedit.o .libs/libtaiqtso_4.0.18_la-idimedit.moc.o .libs/libtaiqtso_4.0.18_la-interceptor.o .libs/libtaiqtso_4.0.18_la-interceptor.moc.o .libs/libtaiqtso_4.0.18_la-qconsole.o .libs/libtaiqtso_4.0.18_la-qconsole.moc.o .libs/libtaiqtso_4.0.18_la-safeptr_so.o .libs/libtaiqtso_4.0.18_la-imisc_so.o .libs/libtaiqtso_4.0.18_la-irenderarea.o .libs/libtaiqtso_4.0.18_la-irenderarea.moc.o .libs/libtaiqtso_4.0.18_la-ibutton.o .libs/libtaiqtso_4.0.18_la-ibutton.moc.o .libs/libtaiqtso_4.0.18_la-iscrollarea.o .libs/libtaiqtso_4.0.18_la-iscrollarea.moc.o .libs/libtaiqtso_4.0.18_la-itextbrowser.o .libs/libtaiqtso_4.0.18_la-itextbrowser.moc.o .libs/libtaiqtso_4.0.18_la-itextedit.o .libs/libtaiqtso_4.0.18_la-itextedit.moc.o .libs/libtaiqtso_4.0.18_la-taiqtso_ti.o
ranlib .libs/libtaiqtso_4.0.18.a
creating libtaiqtso_4.0.18.la
(cd .libs && rm -f libtaiqtso_4.0.18.la && ln -s ../libtaiqtso_4.0.18.la libtaiqtso_4.0.18.la)
make[2]: Leaving directory `/home/jds/emergent/src/temt/taiqtso'
Making all in src/temt/ta
make[2]: Entering directory `/home/jds/emergent/src/temt/ta'
../../temt/maketa/./maketa -hx -css -cpp="g++ -E" -I/home/jds/emergent -I/home/jds/emergent/src/temt/taiqtso -I/home/jds/emergent/src/temt/ta/ios-g++-3.1 -I/home/jds/emergent/src/temt/ta -I/home/jds/emergent/src/temt/css -I/home/jds/emergent/src/emergent/network -I/home/jds/emergent/src/emergent/leabra -I/home/jds/emergent/src/emergent/bp -DSVN_REV=3204 -I/usr/include/qt4 -I/usr/include/qt4/Qt -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL   ta -f files.mta
../../temt/maketa/./maketa: error while loading shared libraries: libode.so: cannot open shared object file: No such file or directory
make[2]: *** [ta_TA.ccx] Error 127
make[2]: Leaving directory `/home/jds/emergent/src/temt/ta'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jds/emergent'
make: *** [all] Error 2

Thanks in advance for any help.

---

### Post by excetara2 on 2008-11-02
Does anyone have any idea what the problem could be?

---

