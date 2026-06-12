---
title: "QT 4 Installation Help"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by kidko on 2006-09-16
All right, I just got a book on QT 4/C++ programming. After putting the CD into the drive and running "sudo ./configure" without a problem, it tells me to run make. So I run "sudo make"... and then I can't install any further:
```
cd src && make -f Makefile
make[1]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src'
cd tools/moc && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/moc'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/moc'
cd tools/rcc && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/rcc'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/rcc'
cd tools/uic && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/uic'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/tools/uic'
cd corelib && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
make -f Makefile.Debug all
make[3]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
make -f Makefile.Release all
make[3]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/corelib'
cd xml && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
make -f Makefile.Debug all
make[3]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
make -f Makefile.Release all
make[3]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/xml'
cd gui && make -f Makefile
make[2]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/gui'
make -f Makefile.Debug all
make[3]: Entering directory `/tmp/qt-x11-opensource-src-4.1.1/src/gui'
g++ -c -pipe -g -fvisibility=hidden -fvisibility-inlines-hidden -Wall -W -D_REENTRANT -fPIC  -DQT_SHARED -DQT_BUILD_GUI_LIB -DQT_NO_CAST_TO_ASCII -DQT3_SUPPORT -DQT_MOC_COMPAT -DQT_RASTER_IMAGEENGINE -DQT_HAVE_SSE -DQT_PDF_SUPPORT -DFT_CONFIG_OPTION_SYSTEM_ZLIB -DQT_NO_STYLE_MAC -DQT_NO_STYLE_WINDOWSXP -DQT_CORE_LIB -D_LARGEFILE64_SOURCE -D_LARGEFILE_SOURCE -I../../mkspecs/linux-g++ -I. -I../../include/QtCore -I../../include -I../../include/QtGui -I../3rdparty/libpng -I../3rdparty/zlib -I../3rdparty/freetype/src -I../3rdparty/freetype/include -I../3rdparty/freetype/builds/unix -I.moc/debug-shared -I/usr/X11R6/include -I. -o .obj/debug-shared/qapplication.o kernel/qapplication.cpp
In file included from ../../include/QtGui/private/qt_x11_p.h:1,
                 from kernel/qapplication.cpp:51:
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:50:22: error: X11/Xlib.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:55:23: error: X11/Xutil.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:56:21: error: X11/Xos.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:63:23: error: X11/Xatom.h: No such file or directory
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:252: error: ‘Colormap’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:253: error: ISO C++ forbids declaration of ‘Visual’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:253: error: expected ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:266: error: ‘Window’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:269: error: ‘Window’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:270: error: ‘Window’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:270: error: ‘Atom’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:271: error: ‘Atom’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:272: error: ‘Window’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:272: error: ‘Atom’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:283: error: expected ‘,’ or ‘...’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:283: error: ISO C++ forbids declaration of ‘XSelectionRequestEvent’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:285: error: ‘Atom’ has not been declared
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:286: error: ‘Atom’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:334: error: ISO C++ forbids declaration of ‘Atom’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:334: error: expected ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:336: error: ISO C++ forbids declaration of ‘Window’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:336: error: expected ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:338: error: ‘Window’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:344: error: ‘Time’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:345: error: ‘Time’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:371: error: ISO C++ forbids declaration of ‘Visual’ with no type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:371: error: expected ‘;’ before ‘*’ token
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:372: error: ‘Colormap’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:524: error: ‘Atom’ does not name a type
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:534: error: ‘FocusOut’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:535: error: ‘FocusIn’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:536: error: ‘KeyPress’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:537: error: ‘KeyRelease’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:538: error: ‘None’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:539: error: ‘RevertToParent’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:540: error: ‘GrayScale’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:541: error: ‘CursorShape’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:556: error: ‘XPoint’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:556: error: template argument 1 is invalid
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:557: error: ‘XRectangle’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:557: error: template argument 1 is invalid
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:558: error: ‘XChar2b’ was not declared in this scope
../../include/QtGui/private/../../../src/gui/kernel/qt_x11_p.h:558: error: template argument 1 is invalid
kernel/qapplication.cpp: In member function ‘void QApplicationPrivate::initialize()’:
kernel/qapplication.cpp:724: warning: unused variable ‘q’
make[3]: *** [.obj/debug-shared/qapplication.o] Error 1
make[3]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/gui'
make[2]: *** [debug-all] Error 2
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src/gui'
make[1]: *** [sub-gui-make_default-ordered] Error 2
make[1]: Leaving directory `/tmp/qt-x11-opensource-src-4.1.1/src'
make: *** [sub-src-make_default-ordered] Error 2

```

Anybody have any idea whatsoever as to what's wrong? I don't know the first thing about what went wrong, and was hoping one of you could help me. The book also doesn't give any advice on troubleshooting. I've tried installing it from the Package Manager, but it doesn't work from there either... "qmake" still isn't a command (even though it should be)

---

