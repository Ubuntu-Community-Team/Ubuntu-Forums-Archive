---
title: "amarok crash on exit"
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Totzo on 2009-02-02
anyone else experiencing this? When I hit exit, amarok crashes and I get this dialogue:

```
A Fatal Error Occurred
The application Amarok (amarok) crashed and caused the signal 6 (SIGABRT).
```

There are no debugging symbols in the details for the crash. Everything seems to be working whilst it's running though. When I start it up again it shows the playlist I had from before the crashes started.

Not a biggy but if I've missed something it would be good to know! :)

---

### Post by DougieFresh4U on 2009-02-02
If you run it from terminal and then exit it, would that maybe show something more?

---

### Post by Totzo on 2009-02-02
I just ran amarok in kde desktop (was using gnome whilst getting the crash) and now it seems to be working fine. Will try it in gnome again and see what happens.

---

### Post by Totzo on 2009-02-02
back in gnome, ran it in the terminal and it spat this out on exit:

```
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3800425
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3800424
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3800422
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3800423
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3800422
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3800429
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x380042a
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3800429
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3800429
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x380042a
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x380042c
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x380042b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3800429
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x380042a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3800429
tim@tim-desktop:~/Desktop$ amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8315) Context::ContextView::clear: "" Line:  165
amarok(8315) Context::ContextView::clear: "" Line:  165
amarok(8315) Context::ContextView::clear: "" Line:  165
amarok(8315) Context::ContextView::clear: "" Line:  165
amarok
amarok(8495) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics()
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(8495) Plasma::Applet::save: saving to "1"
amarok(8495) Context::ContextView::setContainment: "" Line:  599
amarok(8495) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(8495) Plasma::Applet::save: saving to "2"
amarok(8495) Plasma::Applet::save: saving to "3"
amarok(8495) Plasma::Applet::save: saving to "4"
amarok(8495) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8495) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir(QString)
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(8495) MagnatuneConfig::load: load
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3a0000c
QPixmap: Invalid pixmap parameters
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3a00402
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x3a00403
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a00402
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a00402
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x3a00403
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a00405
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a00404
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3a00402
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3a00403
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3a00402
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3a0040a
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x3a0040b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0040a
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0040a
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x3a0040b
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a0040d
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a0040c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3a0040a
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3a0040b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3a0040a
QPixmap: Invalid pixmap parameters
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3a0041d
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x3a0041e
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0041d
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0041d
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x3a0041e
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a00420
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a0041f
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3a0041d
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3a0041e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3a0041d
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3a00424
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x3a00425
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a00424
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a00424
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x3a00425
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a00427
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a00426
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3a00424
QPixmap: Invalid pixmap parameters
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3a00425
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3a00424
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x13c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    152 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x3a0042b
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x3a0042c
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0042b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x3a0042b
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x3a0042c
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a0042e
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x3a0042d
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x3a0042b
X Error: RenderBadPicture (invalid Picture parameter) 170
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x3a0042c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x3a0042b
tim@tim-desktop:~/Desktop$ amarok(8495) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8495) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8495) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8495) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8495) Context::ContextView::clear: "" Line:  165
amarok(8495) Context::ContextView::clear: "" Line:  165
amarok(8495) Context::ContextView::clear: "" Line:  165
amarok(8495) Context::ContextView::clear: "" Line:  165
*** glibc detected *** amarok: corrupted double-linked list: 0x0000000002ad11b0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fc35acd8bbc]
/lib/libc.so.6[0x7fc35acda981]
/lib/libc.so.6(__libc_malloc+0x98)[0x7fc35acdc8b8]
/usr/lib/libQtCore.so.4(_ZN10QByteArray6resizeEi+0xe5)[0x7fc35b7eb735]
/usr/lib/libQtCore.so.4(_ZN16QIODevicePrivateC2Ev+0x206)[0x7fc35b86afe6]
/usr/lib/libQtCore.so.4[0x7fc35b8652a0]
/usr/lib/libQtCore.so.4[0x7fc35b87b079]
/usr/lib/libQtCore.so.4(_ZN14QTemporaryFileC2Ev+0x35)[0x7fc35b87c045]
/usr/lib/libkdecore.so.5(_ZN14KTemporaryFileC1ERK14KComponentData+0x23)[0x7fc35bf06953]
/usr/lib/libkdecore.so.5(_ZN9KLockFile4lockE6QFlagsINS_8LockFlagEE+0x315)[0x7fc35c018735]
/usr/lib/libkdecore.so.5[0x7fc35bec44b8]
/usr/lib/libkdecore.so.5[0x7fc35beb0611]
/usr/lib/libkdecore.so.5(_ZN7KConfig4syncEv+0x358)[0x7fc35beb5d78]
/usr/lib/libkdecore.so.5(_ZN19KCoreConfigSkeleton11writeConfigEv+0xd2)[0x7fc35becfc32]
/usr/lib/libamaroklib.so.1[0x7fc35d3763a3]
/usr/lib/libQtCore.so.4(_ZN14QObjectPrivate14deleteChildrenEv+0x81)[0x7fc35b8de621]
/usr/lib/libQtGui.so.4(_ZN7QWidgetD2Ev+0x15d)[0x7fc35c4a98ed]
/usr/lib/libamaroklib.so.1[0x7fc35d2ccc6e]
/usr/lib/libQtCore.so.4(_ZN14QObjectPrivate14deleteChildrenEv+0x81)[0x7fc35b8de621]
/usr/lib/libQtGui.so.4(_ZN7QWidgetD2Ev+0x15d)[0x7fc35c4a98ed]
/usr/lib/libQtGui.so.4(_ZN9QSplitterD2Ev+0x138)[0x7fc35c805ef8]
/usr/lib/libamaroklib.so.1[0x7fc35d38270e]
/usr/lib/libQtCore.so.4(_ZN14QObjectPrivate14deleteChildrenEv+0x81)[0x7fc35b8de621]
/usr/lib/libQtGui.so.4(_ZN7QWidgetD0Ev+0x15d)[0x7fc35c4a9d8d]
/usr/lib/libQtCore.so.4(_ZN14QObjectPrivate14deleteChildrenEv+0x81)[0x7fc35b8de621]
/usr/lib/libQtGui.so.4(_ZN7QWidgetD2Ev+0x15d)[0x7fc35c4a98ed]
/usr/lib/libkdeui.so.5(_ZN11KMainWindowD2Ev+0x79)[0x7fc35d91cf89]
/usr/lib/libamaroklib.so.1(_ZN10MainWindowD0Ev+0x35e)[0x7fc35d2c828e]
/usr/lib/libamaroklib.so.1(_ZN3AppD1Ev+0x2aa)[0x7fc35d2b4b4a]
amarok[0x404142]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fc35ac7e5a6]
amarok[0x400ea9]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:31 416071                             /usr/bin/amarok
00605000-00606000 r--p 00005000 08:31 416071                             /usr/bin/amarok
00606000-00607000 rw-p 00006000 08:31 416071                             /usr/bin/amarok
022a2000-049f2000 rw-p 022a2000 00:00 0                                  [heap]
41a20000-41a22000 rwxp 00000000 00:0e 723                                /dev/zero
7fc320000000-7fc32008b000 rw-p 7fc320000000 00:00 0 
7fc32008b000-7fc324000000 ---p 7fc32008b000 00:00 0 
7fc3252e7000-7fc3252e8000 ---p 7fc3252e7000 00:00 0 
7fc3252e8000-7fc325ae8000 rwxp 7fc3252e8000 00:00 0 
7fc325ae8000-7fc325ae9000 r-xp 00000000 08:31 955527                     /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv_frames.so
7fc325ae9000-7fc325ce9000 ---p 00001000 08:31 955527                     /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv_frames.so
7fc325ce9000-7fc325cea000 r--p 00001000 08:31 955527                     /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv_frames.so
7fc325cea000-7fc325ceb000 rw-p 00002000 08:31 955527                     /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv_frames.so
7fc325ceb000-7fc325d11000 r-xp 00000000 08:31 417719                     /usr/lib/libwavpack.so.1.0.3
7fc325d11000-7fc325f11000 ---p 00026000 08:31 417719                     /usr/lib/libwavpack.so.1.0.3
7fc325f11000-7fc325f12000 r--p 00026000 08:31 417719                     /usr/lib/libwavpack.so.1.0.3
7fc325f12000-7fc325f13000 rw-p 00027000 08:31 417719                     /usr/lib/libwavpack.so.1.0.3
7fc325f13000-7fc325f16000 r-xp 00000000 08:31 955529                     /usr/lib/xine/plugins/1.25/xineplug_wavpack.so
7fc325f16000-7fc326115000 ---p 00003000 08:31 955529                     /usr/lib/xine/plugins/1.25/xineplug_wavpack.so
7fc326115000-7fc326116000 r--p 00002000 08:31 955529                     /usr/lib/xine/plugins/1.25/xineplug_wavpack.so
7fc326116000-7fc326117000 rw-p 00003000 08:31 955529                     /usr/lib/xine/plugins/1.25/xineplug_wavpack.so
7fc326117000-7fc32611e000 r-xp 00000000 08:31 955525                     /usr/lib/xine/plugins/1.25/xineplug_dmx_sputext.so
7fc32611e000-7fc32631d000 ---p 00007000 08:31 955525                     /usr/lib/xine/plugins/1.25/xineplug_dmx_sputext.so
7fc32631d000-7fc32631e000 r--p 00006000 08:31 955525                     /usr/lib/xine/plugins/1.25/xineplug_dmx_sputext.so
7fc32631e000-7fc32631f000 rw-p 00007000 08:31 955525                     /usr/lib/xine/plugins/1.25/xineplug_dmx_sputext.so
7fc32631f000-7fc326321000 r-xp 00000000 08:31 955460                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_elem.so
7fc326321000-7fc326520000 ---p 00002000 08:31 955460                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_elem.so
7fc326520000-7fc326521000 r--p 00001000 08:31 955460                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_elem.so
7fc326521000-7fc326522000 rw-p 00002000 08:31 955460                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_elem.so
7fc326522000-7fc32656a000 r-xp 00000000 08:31 416878                     /usr/lib/libFLAC.so.8.2.0
7fc32656a000-7fc32676a000 ---p 00048000 08:31 416878                     /usr/lib/libFLAC.so.8.2.0
7fc32676a000-7fc32676b000 r--p 00048000 08:31 416878                     /usr/lib/libFLAC.so.8.2.0
7fc32676b000-7fc32676c000 rw-p 00049000 08:31 416878                     /usr/lib/libFLAC.so.8.2.0
7fc32676c000-7fc32676f000 r-xp 00000000 08:31 955528                     /usr/lib/xine/plugins/1.25/xineplug_flac.so
7fc32676f000-7fc32696e000 ---p 00003000 08:31 955528                     /usr/lib/xine/plugins/1.25/xineplug_flac.so
7fc32696e000-7fc32696f000 r--p 00002000 08:31 955528                     /usr/lib/xine/plugins/1.25/xineplug_flac.so
7fc32696f000-7fc326970000 rw-p 00003000 08:31 955528                     /usr/lib/xine/plugins/1.25/xineplug_flac.so
7fc326970000-7fc326972000 r-xp 00000000 08:31 955522                     /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
7fc326972000-7fc326b71000 ---p 00002000 08:31 955522                     /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
7fc326b71000-7fc326b72000 r--p 00001000 08:31 955522                     /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
7fc326b72000-7fc326b73000 rw-p 00002000 08:31 955522                     /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
7fc326b73000-7fc326b77000 r-xp 00000000 08:31 955458                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
7fc326b77000-7fc326d76000 ---p 00004000 08:31 955458                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
7fc326d76000-7fc326d77000 r--p 00003000 08:31 955458                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
7fc326d77000-7fc326d78000 rw-p 00004000 08:31 955458                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
7fc326d78000-7fc326d7c000 r-xp 00000000 08:31 955461                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_pes.so
7fc326d7c000-7fc326f7b000 ---p 00004000 08:31 955461                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_pes.so
7fc326f7b000-7fc326f7c000 r--p 00003000 08:31 955461                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_pes.so
7fc326f7c000-7fc326f7d000 rw-p 00004000 08:31 955461                     /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_pes.so
7fc326f7d000-7fc326f7f000 r-xp 00000000 08:31 955511                     /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
7fc326f7f000-7fc32717e000 ---p 00002000 08:31 955511                     /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
7fc32717e000-7fc32717f000 r--p 00001000 08:31 955511                     /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
7fc32717f000-7fc327180000 rw-p 00002000 08:31 955511                     /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
7fc327180000-7fc32718a000 r-xp 00000000 08:31 955508                     /usr/lib/xine/plugins/1.25/xineplug_dmx_asf.so
7fc32718a000-7fc32738a000 ---p 0000a000 08:31 955508                     /usr/lib/xine/plugins/1.25/xineplug_dmx_asf.so
7fc32738a000-7fc32738b000 r--p 0000a000 08:31 955508                     /usr/lib/xine/plugins/1.25/xineplug_dmx_asf.so
7fc32738b000-7fc32738c000 rw-p 0000b000 08:31 955508                     /usr/lib/xine/plugins/1.25/xineplug_dmx_asf.so
7fc32738c000-7fc3273d4000 r-xp 00000000 08:31 417462                     /usr/lib/libmodplug.so.0.0.0
7fc3273d4000-7fc3275d4000 ---p 00048000 08:31 417462                     /usr/lib/libmodplug.so.0.0.0
7fc3275d4000-7fc3275d5000 r--p 00048000 08:31 417462                     /usr/lib/libmodplug.so.0.0.0
7fc3275d5000-7fc3275d8000 rw-p 00049000 08:31 417462                     /usr/lib/libmodplug.so.0.0.0
7fc3275d8000-7fc327658000 rw-p 7fc3275d8000 00:00 0 
7fc327658000-7fc32766a000 r-xp 00000000 08:31 955509                     /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
7fc32766a000-7fc32786a000 ---p 00012000 08:31 955509                     /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
7fc32786a000-7fc32786b000 r--p 00012000 08:31 955509                     /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
7fc32786b000-7fc32786c000 rw-p 00013000 08:31 955509                     /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
7fc32786c000-7fc327871000 r-xp 00000000 08:31 955523                     /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
7fc327871000-7fc327a71000 ---p 00005000 08:31 955523                     /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
7fc327a71000-7fc327a72000 r--p 00005000 08:31 955523                     /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
7fc327a72000-7fc327a73000 rw-p 00006000 08:31 955523                     /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
7fc327a73000-7fc327a7f000 r-xp 00000000 08:31 955513                     /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
7fc327a7f000-7fc327c7e000 ---p 0000c000 08:31 955513                     /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
7fc327c7e000-7fc327c7f000 r--p 0000b000 08:31 955513                     /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
7fc327c7f000-7fc327c800KCrash: Application 'amarok' crashing...
sock_file=/home/tim/.kde/socket-tim-desktop/kdeinit4__0
tim@tim-desktop:~/Desktop$ 

```

any ideas?

---

