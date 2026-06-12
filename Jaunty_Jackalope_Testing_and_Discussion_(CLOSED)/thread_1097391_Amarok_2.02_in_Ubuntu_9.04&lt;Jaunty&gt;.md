---
title: "Amarok 2.02 in Ubuntu 9.04&lt;Jaunty&gt;"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by all4him on 2009-03-15
Hello everyone,

Just a question, I get no sound out of the speakers from Amarok.  It states that it is playing, no sound.

I know that this is in Alpha..   Just trying to see what the deal is..

Thanks for your time and attention..

---

### Post by kodiakmax on 2009-03-15
I had issues with it as well.

You need to install:

systemsettings
FFMPEG
gstreamer0.10-ffmpeg
libxine1-ffmpeg

Then run systemsettings
open the multimedia button
click on the backend tab
move xine to the top of the list
click apply

Hopefully things should then be working

---

### Post by overdrank on 2009-03-15
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by Skalman5 on 2009-03-31
This is how i fixed it:

1. Start synaptic package manager
2. Remove phonon-backend-gstreamer (will also uninstall amarok)
3. Install phonon-backend-xine
4. Reboot (Don&#7831; know if this is necessary)
5. Install amarok via synaptic.
6. Reboot

All thanks to this post:
[http://kubuntuforums.net/forums/index.php?topic=3100214]("http://kubuntuforums.net/forums/index.php?topic=3100214")

---

### Post by Laidibug on 2009-04-03
Thanx Skalman. Works for me. If you install the xine backend first and then remove the gstreamer backend it won't uninstall amarok. Worked after reboot.

---

### Post by mlissner on 2009-04-17
I think that's a bit overkill. If you install systemsettings and phonon-backend-xine, you can set xine to be the backend, and then you're good to go with a restart of amarok. No need to remove amarok or phonon-backend-gstreamer.

---

