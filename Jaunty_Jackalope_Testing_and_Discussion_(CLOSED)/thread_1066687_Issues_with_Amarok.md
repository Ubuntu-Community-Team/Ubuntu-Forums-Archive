---
title: "Issues with Amarok"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Elfy on 2009-02-11
I have an odd one with amarok or at least I think so - can't find the same issue here anyway .

I have tried both the amarok in the normal repos and the amarok in the ppa.

With the normal version - on restart the previously current playlist disappears and while sound worked before it was restarted it refuses to do so once it's restarted.

With the ppa version the playlist now shows the current one but has the same issue with sound on a restart.

I've deleted the configs in between purging and reinstalling.

Rhythmbox doesn't have the saem sound issue on reboot so I don't think that 
amarok is stopping the sound as such just not working.

Is anyone else seeing the same problem?

Currently up to date with any updates on alpha4.

I have an issue with pulse audio that might be important - I have to add tsched=0 to the load-module module-hal-detect line of /etc/pulse/default.pa and changed the default-fragment-size-msec from 10 to 5 in the daemon.conf to stop stuttering.

I also get the amarok crashing on quit.

Edit - forgot to add this

```
amarok(6972) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
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
amarok(6972) Plasma::Applet::save: saving to "1"
amarok(6972) Context::ContextView::setContainment: "" Line:  599
amarok(6972) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(6972) Plasma::Applet::save: saving to "2"
amarok(6972) Plasma::Applet::save: saving to "3"
amarok(6972) Plasma::Applet::save: saving to "4"
amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6972) Context::ColumnContainment::insertInGrid: "" Line:  603
amarok(6972) Context::ColumnContainment::insertInGrid: "" Line:  603
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
amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kevin@kevin-desktop:~$ amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QPixmap: Invalid pixmap parameters
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode: 53 (X_CreatePixmap)
  Resource id:  0x32b
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    153 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x44004f3
X Error: RenderBadPicture (invalid Picture parameter) 173
  Extension:    153 (RENDER)
  Minor opcode: 8 (RenderComposite)
  Resource id:  0x44004f4
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x44004f3
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x44004f3
X Error: RenderBadPicture (invalid Picture parameter) 173
  Extension:    153 (RENDER)
  Minor opcode: 5 (RenderChangePicture)
  Resource id:  0x44004f4
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x44004f6
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x44004f5
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 73 (X_GetImage)
  Resource id:  0x44004f3
X Error: RenderBadPicture (invalid Picture parameter) 173
  Extension:    153 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x44004f4
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x44004f3
amarok(6972) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6972) Context::ContextView::clear: "" Line:  165
amarok(6972) Context::ContextView::clear: "" Line:  165
amarok(6972) Context::ContextView::clear: "" Line:  165
amarok(6972) Context::ContextView::clear: "" Line:  165
*** glibc detected *** amarok: corrupted double-linked list: 0x08825cf8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6aec5a4]
/lib/tls/i686/cmov/libc.so.6[0xb6aef572]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb6af0965]
/usr/lib/libstdc++.so.6(_Znwj+0x27)[0xb694df37]
/usr/lib/libQtXml.so.4[0xb66c7317]
/usr/lib/libQtXml.so.4(_ZN12QDomDocument13createElementERK7QString+0x32)[0xb66c73c2]
/usr/lib/libamaroklib.so.1(_ZN4Meta12XSPFPlaylist12setTrackListE5QListI10KSharedPtrINS_5TrackEEEb+0xb4e)[0xb6d8bf1e]
/usr/lib/libamaroklib.so.1(_ZN4Meta12XSPFPlaylistC1E5QListI10KSharedPtrINS_5TrackEEE+0x29e)[0xb6d8d77e]
/usr/lib/libamaroklib.so.1[0xb6df4148]
/usr/lib/libamaroklib.so.1(_ZN8Playlist5ModelD0Ev+0x216)[0xb6cf4476]
/usr/lib/libamaroklib.so.1(_ZN8Playlist5Model7destroyEv+0x2b)[0xb6cecfeb]
/usr/lib/libamaroklib.so.1(_ZN3AppD1Ev+0x2cb)[0xb6e3393b]
amarok[0x804c04c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6a93775]
amarok[0x8048b21]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:25 441046     /usr/bin/amarok
0804e000-0804f000 r--p 00005000 08:25 441046     /usr/bin/amarok
0804f000-08050000 rw-p 00006000 08:25 441046     /usr/bin/amarok
08157000-0a5f5000 rw-p 08157000 00:00 0          [heap]
9d78b000-9d78c000 ---p 9d78b000 00:00 0 
9d78c000-9df8c000 rwxp 9d78c000 00:00 0 
9df8c000-9dfd3000 r-xp 00000000 08:25 440752     /usr/lib/libmodplug.so.0.0.0
9dfd3000-9dfd4000 r--p 00047000 08:25 440752     /usr/lib/libmodplug.so.0.0.0
9dfd4000-9dfd7000 rw-p 00048000 08:25 440752     /usr/lib/libmodplug.so.0.0.0
9dfd7000-9e057000 rw-p 9dfd7000 00:00 0 
9e057000-9e3dd000 r-xp 00000000 08:25 442410     /usr/lib/libsmbclient.so.0
9e3dd000-9e3e4000 r--p 00386000 08:25 442410     /usr/lib/libsmbclient.so.0
9e3e4000-9e3e9000 rw-p 0038d000 08:25 442410     /usr/lib/libsmbclient.so.0
9e3e9000-9e3ea000 rw-p 9e3e9000 00:00 0 
9e3f1000-9e44b000 r--p 00000000 08:25 27838      /home/kevin/.fonts/arial.ttf
9e44b000-9e46b000 rw-s 00000000 00:09 1736737    /SYSV0056a4d6 (deleted)
9e46b000-9e481000 r-xp 00000000 08:25 442990     /usr/lib/libmad.so.0.2.1
9e481000-9e482000 r--p 00015000 08:25 442990     /usr/lib/libmad.so.0.2.1
9e482000-9e483000 rw-p 00016000 08:25 442990     /usr/lib/libmad.so.0.2.1
9e484000-9e494000 rw-s 00000000 00:0e 5216       /dev/snd/pcmC0D0p
9e494000-9e496000 r-xp 00000000 08:25 17569      /usr/lib/xine/plugins/1.25/xineplug_decode_mad.so
9e496000-9e497000 r--p 00001000 08:25 17569      /usr/lib/xine/plugins/1.25/xineplug_decode_mad.so
9e497000-9e498000 rw-p 00002000 08:25 17569      /usr/lib/xine/plugins/1.25/xineplug_decode_mad.so
9e498000-9e49a000 r-xp 00000000 08:25 17637      /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
9e49a000-9e49b000 r--p 00001000 08:25 17637      /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
9e49b000-9e49c000 rw-p 00002000 08:25 17637      /usr/lib/xine/plugins/1.25/xineplug_dmx_rawdv.so
9e49c000-9e4a0000 r-xp 00000000 08:25 17573      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
9e4a0000-9e4a1000 ---p 00004000 08:25 17573      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
9e4a1000-9e4a2000 r--p 00004000 08:25 17573      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
9e4a2000-9e4a3000 rw-p 00005000 08:25 17573      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg.so
9e4a3000-9e4a5000 r-xp 00000000 08:25 17639      /usr/lib/xine/plugins/1.25/xineplug_dmx_slave.so
9e4a5000-9e4a6000 r--p 00001000 08:25 17639      /usr/lib/xine/plugins/1.25/xineplug_dmx_slave.so
9e4a6000-9e4a7000 rw-p 00002000 08:25 17639      /usr/lib/xine/plugins/1.25/xineplug_dmx_slave.so
9e4a7000-9e4a9000 r-xp 00000000 08:25 17641      /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv4mpeg2.so
9e4a9000-9e4aa000 r--p 00001000 08:25 17641      /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv4mpeg2.so
9e4aa000-9e4ab000 rw-p 00002000 08:25 17641      /usr/lib/xine/plugins/1.25/xineplug_dmx_yuv4mpeg2.so
9e4ab000-9e4b3000 r-xp 00000000 08:25 17636      /usr/lib/xine/plugins/1.25/xineplug_dmx_qt.so
9e4b3000-9e4b4000 r--p 00007000 08:25 17636      /usr/lib/xine/plugins/1.25/xineplug_dmx_qt.so
9e4b4000-9e4b5000 rw-p 00008000 08:25 17636      /usr/lib/xine/plugins/1.25/xineplug_dmx_qt.so
9e4b5000-9e4b7000 r-xp 00000000 08:25 17632      /usr/lib/xine/plugins/1.25/xineplug_dmx_mng.so
9e4b7000-9e4b8000 r--p 00001000 08:25 17632      /usr/lib/xine/plugins/1.25/xineplug_dmx_mng.so
9e4b8000-9e4b9000 rw-p 00002000 08:25 17632      /usr/lib/xine/plugins/1.25/xineplug_dmx_mng.so
9e4b9000-9e4bb000 r-xp 00000000 08:25 17633      /usr/lib/xine/plugins/1.25/xineplug_dmx_nsv.so
9e4bb000-9e4bc000 r--p 00001000 08:25 17633      /usr/lib/xine/plugins/1.25/xineplug_dmx_nsv.so
9e4bc000-9e4bd000 rw-p 00002000 08:25 17633      /usr/lib/xine/plugins/1.25/xineplug_dmx_nsv.so
9e4bd000-9e4c4000 r-xp 00000000 08:25 17625      /usr/lib/xine/plugins/1.25/xineplug_dmx_avi.so
9e4c4000-9e4c5000 r--p 00006000 08:25 17625      /usr/lib/xine/plugins/1.25/xineplug_dmx_avi.so
9e4c5000-9e4c6000 rw-p 00007000 08:25 17625      /usr/lib/xine/plugins/1.25/xineplug_dmx_avi.so
9e4c6000-9e4c8000 r-xp 00000000 08:25 17635      /usr/lib/xine/plugins/1.25/xineplug_dmx_pva.so
9e4c8000-9e4c9000 r--p 00001000 08:25 17635      /usr/lib/xine/plugins/1.25/xineplug_dmx_pva.so
9e4c9000-9e4ca000 rw-p 00002000 08:25 17635      /usr/lib/xine/plugins/1.25/xineplug_dmx_pva.so
9e4ca000-9e4cd000 r-xp 00000000 08:25 17627      /usr/lib/xine/plugins/1.25/xineplug_dmx_flv.so
9e4cd000-9e4ce000 ---p 00003000 08:25 17627      /usr/lib/xine/plugins/1.25/xineplug_dmx_flv.so
9e4ce000-9e4cf000 r--p 00003000 08:25 17627      /usr/lib/xine/plugins/1.25/xineplug_dmx_flv.so
9e4cf000-9e4d0000 rw-p 00004000 08:25 17627      /usr/lib/xine/plugins/1.25/xineplug_dmx_flv.so
9e4d0000-9e4d2000 r-xp 00000000 08:25 17626      /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
9e4d2000-9e4d3000 r--p 00001000 08:25 17626      /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
9e4d3000-9e4d4000 rw-p 00002000 08:25 17626      /usr/lib/xine/plugins/1.25/xineplug_dmx_fli.so
9e4d4000-9e4d5000 ---p 9e4d4000 00:00 0 
9e4d5000-9ecd5000 rwxp 9e4d5000 00:00 0 
9ecd5000-9ecd6000 ---p 9ecd5000 00:00 0 
9ecd6000-9f4d6000 rwxp 9ecd6000 00:00 0 
9f4d6000-9f6a3000 rw-p 9f4d6000 00:00 0 
9f6a3000-9f6a4000 ---p 9f6a3000 00:00 0 
9f6a4000-9fea4000 rwxp 9f6a4000 00:00 0 
9fea4000-a028d000 rw-p 9fea4000 00:00 0 
a028d000-a028e000 ---p a028d000 00:00 0 
a028e000-a0a8e000 rwxp a028e000 00:00 0 
a0a8e000-a0e99000 rw-p a0a8e000 00:00 0 
a0e99000-a0e9a000 r-xp 00000000 08:25 17601      /usr/lib/xine/plugins/1.25/xineplug_vo_out_none.so
a0e9a000-a0e9b000 r--p 00000000 08:25 17601      /usr/lib/xine/plugins/1.25/xineplug_vo_out_none.so
a0e9b000-a0e9c000 rw-p 00001000 08:25 17601      /usr/lib/xine/plugins/1.25/xineplug_vo_out_none.so
a0e9c000-a0f19000 r--p 00000000 08:25 580971     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
a0f19000-a8796000 rw-s 00000000 08:25 99440      /var/tmp/kdecache-kevin/kpc/amarok.data
a8796000-aa7af000 rw-s 00000000 08:25 99437      /var/tmp/kdecache-kevin/kpc/amarok.index
aacac000-ab3a5000 r-xp 00000000 08:25 20253      /usr/lib/kde4/plugins/script/libqtscript_gui.so
ab3a5000-ab3bb000 r--p 006f8000 08:25 20253      /usr/lib/kde4/plugins/script/libqtscript_gui.so
ab3bb000-ab3c1000 rw-p 0070e000 08:25 20253      /usr/lib/kde4/plugins/script/libqtscript_gui.so
ab3c1000-ab3c2000 ---p ab3c1000 00:00 0 
ab3c2000-abbc2000 rwxp ab3c2000 00:00 0 
abbc2000-abbc3000 ---p abbc2000 00:00 0 
abbc3000-ac3c3000 rwxp abbc3000 00:00 0 
ac3c6000-ac3ce000 r-xp 00000000 08:25 17631      /usr/lib/xine/plugins/1.25/xineplug_dmx_matroska.so
ac3ce000-ac3cf000 r--p 00007000 08:25 17631      /usr/lib/xine/plugins/1.25/xineplug_dmx_matroska.so
ac3cf000-ac3d0000 rw-p 00008000 08:25 17631      /usr/lib/xine/plugins/1.25/xineplug_dmx_matroska.so
ac3d0000-ac3d4000 r-xp 00000000 08:25 17574      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_block.so
ac3d4000-ac3d5000 r--p 00003000 08:25 17574      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_block.so
ac3d5000-ac3d6000 rw-p 00004000 08:25 17574      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_block.so
ac3d6000-ac3e5000 r-xp 00000000 08:25 17624      /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
ac3e5000-ac3e6000 r--p 0000e000 08:25 17624      /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
ac3e6000-ac3e7000 rw-p 0000f000 08:25 17624      /usr/lib/xine/plugins/1.25/xineplug_dmx_audio.so
ac3e7000-ac3ed000 r-xp 00000000 08:25 17638      /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
ac3ed000-ac3ee000 r--p 00005000 08:25 17638      /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
ac3ee000-ac3ef000 rw-p 00006000 08:25 17638      /usr/lib/xine/plugins/1.25/xineplug_dmx_real.so
ac3ef000-ac3fa000 r-xp 00000000 08:25 17628      /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
ac3fa000-ac3fb000 r--p 0000a000 08:25 17628      /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
ac3fb000-ac3fc000 rw-p 0000b000 08:25 17628      /usr/lib/xine/plugins/1.25/xineplug_dmx_games.so
ac3fc000-ac400000 r-xp 00000000 08:25 17576      /usr/lib/xine/plugins/1.25/xineplug_dmx_mpeg_pes.so
ac400000-ac401000 ---p 00004000 08:25 17576      /KCrash: Application 'amarok' crashing...
sock_file=/home/kevin/.kde/socket-kevin-desktop/kdeinit4__0

```

Edit - not at all sure which actual update dealt with this - but after trying amarok every week since posting this it now appears to work properly.
Each time there's a pulseaudio update I change the 2 files back to default - then have to change them back to the altered state.

---

