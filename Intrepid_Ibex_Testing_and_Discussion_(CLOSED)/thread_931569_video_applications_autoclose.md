---
title: "video applications autoclose"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by magicmanfk on 2008-09-27
Once I installed the default gstreamer codecs, any media app will close immediately after it opens to play avi files. I tried mplayer, vlc, and totem. Any suggestions on why this is occurring? I'm using intrepid with an ati x1300 mobility graphics card.

Here's output when trying to open it through VLC (the error part, at least):

/usr/bin/pulseaudio: error while loading shared libraries: libpulsecore.so.5: cannot open shared object file: No such file or directory
/usr/bin/pulseaudio: error while loading shared libraries: libpulsecore.so.5: cannot open shared object file: No such file or directory
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

(process:7498): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:7498): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(process:7498): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:7498): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by sayantandas on 2008-10-13
i am getting the exact same error while playing video files.
mp3 plays fine. flash movies online work just fine. but videos wont play

any idea ??

---

### Post by sayantandas on 2008-10-21
i think i have found the solution.
it was the video driver.
just install the new restricted video driver. and it works all fine now..:guitar:

---

