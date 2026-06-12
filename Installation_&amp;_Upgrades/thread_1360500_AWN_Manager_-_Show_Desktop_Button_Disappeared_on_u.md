---
title: "AWN Manager - Show Desktop Button Disappeared on upgrade to 9.10"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by sebastianrimbaud on 2009-12-21
When I upgraded to 9.10, my AWN manager no longer showed the "Show Desktop" button.

I've tried activating and deactivating it. I've tried to reinstall it, since it worked fine in 9.04. 

All it shows is a white line, where the button would be, and it will sometimes say something about "Show.desktop" error or something. I don't know how to reproduce it. Is there a way to find out if it's a missing file or something that is making it mess up?

Can someone please help? It's been bugging me since I've upgraded.

---

### Post by darco on 2009-12-21
Try uninstalling/reinstalling.....better yet make sure you have the latest AWN

[http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html](http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html)

good luck

darco

---

### Post by sebastianrimbaud on 2009-12-22
I tried that, it didn't fix it.

I found out how to open it using terminal to determine what's going on when it opens.

> sebastianrimbaud@foreigner:~$ avant-window-navigator &
[1] 11516
sebastianrimbaud@foreigner:~$ 
(awn-applets-migration:11517): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/showdesktop.desktop

** (showdesktop.py:11522): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (showdesktop.py:11522): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (showdesktop.py:11522): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
LOADED : /usr/share/applications/firefox.desktop
FAILED : /home/sebastianrimbaud/Desktop/openoffice.org-writer.desktop
FAILED : /home/sebastianrimbaud/Desktop/rhythmbox.desktop
LOADED : /usr/share/applications/thunderbird.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/skype.desktop
LOADED : /usr/share/applications/gwibber.desktop
LOADED : /usr/share/applications/kde4/ktorrent.desktop
LOADED : /usr/share/applications/openoffice.org-writer.desktop
LOADED : /usr/share/applications/gimp.desktop
LOADED : /usr/share/applications/scribus.desktop
LOADED : /usr/share/applications/comix.desktop
LOADED : /usr/share/applications/banshee-1.desktop
LOADED : /usr/share/applications/vlc.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
FAILED : /home/sebastianrimbaud/Pictures/RealPictures/IMG_1545.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1546.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1547.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1549.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1550.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1551.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1553.JPG
file:///home/sebastianrimbaud/Pictures/RealPictures/IMG_1554.JPG

FAILED : /home/sebastianrimbaud/Desktop/f-spot.desktop
FAILED : /usr/share/applications/songbird.desktop
LOADED : /usr/share/applications/chromium-browser.desktop
FAILED : /home/sebastianrimbaud/Desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
APPLET : /usr/share/avant-window-navigator/applets/places.desktop
APPLET : /usr/share/avant-window-navigator/applets/shinyswitcher.desktop
APPLET : /usr/share/avant-window-navigator/applets/plugger.desktop
APPLET : /usr/share/avant-window-navigator/applets/trash.desktop
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
cols = 1,  rows=1 
^C


I did some fiddling with modifying the launchers to get rid of the FAILED ones and came up with this afterward.

> sebastianrimbaud@foreigner:~$ avant-window-navigator &
[1] 11719
sebastianrimbaud@foreigner:~$ 
(awn-applets-migration:11720): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/showdesktop.desktop

** (showdesktop.py:11725): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (showdesktop.py:11725): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (showdesktop.py:11725): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/thunderbird.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/skype.desktop
LOADED : /usr/share/applications/gwibber.desktop
LOADED : /usr/share/applications/kde4/ktorrent.desktop
LOADED : /usr/share/applications/openoffice.org-writer.desktop
LOADED : /usr/share/applications/gimp.desktop
LOADED : /usr/share/applications/scribus.desktop
LOADED : /usr/share/applications/comix.desktop
LOADED : /usr/share/applications/banshee-1.desktop
LOADED : /usr/share/applications/vlc.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/chromium-browser.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/places.desktop

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
APPLET : /usr/share/avant-window-navigator/applets/shinyswitcher.desktop
APPLET : /usr/share/avant-window-navigator/applets/plugger.desktop
APPLET : /usr/share/avant-window-navigator/applets/trash.desktop
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
cols = 1,  rows=1 



Any ideas on what the fix could be? Please?

---

### Post by Todamont on 2011-01-24
solved? I lost the desktop icon in AWN on updgrade to 10.04 from 9.10. Is there any easy fix? I don't see how to easily add it back into AWN...

---

