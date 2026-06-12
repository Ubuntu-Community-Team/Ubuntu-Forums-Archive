---
title: "Amarok 2"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Quift on 2009-03-24
Hi,

I upgraded yesterday and after having spent a few hours solving a graphical drivers issue, and the flash functioin for firefox I'm now trying to solve some problems with Amarok2.

I used Amarok 2 even before the upgrade and seems to be one of the few who acutally like it. . Maybe because I', using a nice and clean grey theme on gnome, making Amarok 2 a visual fit...

Anyway. It now refuses to play any songs!

The Library loads as it did before, and the playlists are handled normally, but I cannot get it tp play any songs. Instead I get a small notification which says:

Too many errors in playlist. Playback stopped.

I have installed the extra codecs through synaptic, and rebooted, but all to no avail. Is there anything simple I have missed?

Thanks for all advice.

/Quift

---

### Post by Bakon Jarser on 2009-03-24
Have you tried uninstalling and reinstalling?

---

### Post by Kevbert on 2009-03-24
I was going to suggest that you try entering
```
amarok
```
in konsole/terminal, but if you do that you may get other errors, like this (even though mine works from the program launcher):
```
$ amarok
amarok(8373) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692                                                                                                                             
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
amarok(8373) Plasma::Applet::save: saving to "1"
amarok(8373) Context::ContextView::setContainment: "" Line:  599
amarok(8373) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(8373) Plasma::Applet::save: saving to "2"
amarok(8373) Plasma::Applet::save: saving to "3"
amarok(8373) Plasma::Applet::save: saving to "4"
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) Context::ColumnContainment::insertInGrid: "" Line:  603
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
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(8373) MagnatuneConfig::load: load
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kevin@kevin-dt1b:~$ QPainter::begin: Cannot paint on a null pixmap
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(8373) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated


```
I've raised a [COLOR="Red"][bug report]("https://bugs.launchpad.net/ubuntu/+source/amarok2/+bug/348104")[/COLOR] on these errors as this shouldn't happen.

---

### Post by Quift on 2009-03-24
pierre-emil@pierre-emil-laptop:~$ amarok
amarok(20224) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
QDBusObjectPath: invalid path ""
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
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
amarok(20224) Plasma::Applet::save: saving to "1"
amarok(20224) Context::ContextView::setContainment: "" Line:  599
amarok(20224) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(20224) Plasma::Applet::save: saving to "2"
amarok(20224) Plasma::Applet::save: saving to "3"
amarok(20224) Plasma::Applet::save: saving to "4"
amarok(20224) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(20224) Context::ColumnContainment::insertInGrid: "" Line:  603
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
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(20224) MagnatuneConfig::load: load
amarok(20224) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(20224) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(20224) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
pierre-emil@pierre-emil-laptop:~$ amarok(20224) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated

---

### Post by Kevbert on 2009-03-24
Looks like that invalid path is the problem near the top.
I made a link to here in the launchpad bug report.

---

### Post by Quift on 2009-03-24
I actually got that error in intrepid aswell, but then it still worked fine exept the annoying pop-up telling me something was missing.

---

### Post by hockeyhead019 on 2009-03-24
this is y i've yet to upgrade haha as amarok 2 is my main media player and i think i might explode if i don't have music haha... but i haven't seen anybody with a solution to the amarok player problems for jaunty

---

### Post by Flarkis on 2009-03-24
@Quift
I noticed you mentioned about installing codecs. One of the wonderfull things of amarok is the new phonon backend for multimedia. Do you have phonon-backend-xine installed? There is a gstreamer backend but it is not as functional.

---

### Post by keithpeter on 2009-03-29
> **Kevbert said:**
> Looks like that invalid path is the problem near the top.
I made a link to here in the launchpad bug report.

Me too. Installed Jaunty no problem, added the ubuntu-restricted, can play mp3s fine in movie player but not Amarok.

```
keith@quiet:~$ amarok
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:585: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Dust Sand/gtk-2.0/gtkrc:586: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
amarok(5524) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
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
amarok(5524) Plasma::Applet::save: saving to "1"
amarok(5524) Context::ContextView::setContainment: "" Line:  599
amarok(5524) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(5524) Plasma::Applet::save: saving to "2"
amarok(5524) Plasma::Applet::save: saving to "3"
amarok(5524) Plasma::Applet::save: saving to "4"
amarok(5524) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5524) Context::ColumnContainment::insertInGrid: "" Line:  603
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
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(5524) MagnatuneConfig::load: load
amarok(5524) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5524) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(5524) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QPainter::begin: Cannot paint on a null pixmap

```

---

### Post by xtoudi on 2009-03-29
All of you - like said Flarkis: install **phonon-backend-xine** and that's all.
But take a look on other music players - seriously!! Amarok 2.0.2 has still too many bugs.
**Songbird** is perfect to me - a lot of themes, plugins and only about 30MB !!!!!.

---

### Post by keithpeter on 2009-03-29
> **xtoudi said:**
> All of you - like said Flarkis: install **phonon-backend-xine** and that's all.


Thanks, but showing as already installed in synaptic...

---

### Post by xtoudi on 2009-03-29
> **keithpeter said:**
> Thanks, but showing as already installed in synaptic...

Wierd ... usually works. That's another cause why I don't use Amarok 2.0.2 although I really like it - **usually** works.
Hmmm ... so I don't know. I assume install a whole ubuntu-restricted-extras resolve problem ... but will install tons rubbish too :)

---

### Post by ahepas on 2009-04-03
> **keithpeter said:**
> Thanks, but showing as already installed in synaptic...

hello. same here. i have all dependencies installed and still no sound! songbird, rhythmbox, vlc working fine.


jaunty beta amd64

---

### Post by dawbomb on 2009-04-03
Yip, I've got the same issue.  Can play MP3's in vlc, rhythmbox, totem etc, but nothing in Amarok2.  Which is a pity, cos its the best of the lot!

Same thing on both my desktop and my laptop, both are running Jaunty Beta 32bit desktop.

---

### Post by constantinosm on 2009-04-04
At the command line type:

sudo apt-get install libxine1-ffmpeg

---

### Post by dawbomb on 2009-04-04
> **constantinosm said:**
> At the command line type:

sudo apt-get install libxine1-ffmpeg

Aah fantastic!  And all of a sudden it works!  Thanks alot!!!  :D

So basically the makers of amarok just need to add libxine1-ffmpeg to the dependency list...  Silly them for excluding it!

---

### Post by Slystone on 2009-04-08
Same here, Amarok won't launch. The French met the same bug: [http://forum.ubuntu-fr.org/viewtopic.php?id=300368](http://forum.ubuntu-fr.org/viewtopic.php?id=300368)

I'll keep and eye on both threads, it will hopefully soon be patched.

Edit : Constantinosm, I've tried your solution and in my case it's no good... libxine1-ffmpeg already installed -and I have phonon and all the other packages.

---

### Post by skedone on 2009-04-08
constantinosm your a star mate that worked

---

