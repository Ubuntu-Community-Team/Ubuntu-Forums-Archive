---
title: "Audio really choppy on divx, give it a try!"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-03-09
I'm trying to watch a divx, but the audio is really choppy. If I transcode it to xvid everything is ok for me.

I will attach a portion of the video (512k only) so you can test it, and tell me if you have my problem too.

This is my gstreamer setup:
```
ii  gstreamer0.10-alsa                        0.10.22-3                            GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                      0.10.6-1                             FFmpeg plugin for GStreamer
ii  gstreamer0.10-gnomevfs                    0.10.22-3                            GStreamer plugin for GnomeVFS
ii  gstreamer0.10-pitfdll                     0.9.1.1+cvs20080215-1ubuntu1         GStreamer plugin for using MS Windows binary
ii  gstreamer0.10-plugins-bad                 0.10.10-1ubuntu1                     GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-base                0.10.22-3                            GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.22-3                            GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                0.10.14-1                            GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                0.10.10-1build1                      GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse     0.10.7-2                             GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-pulseaudio                  0.10.14-1                            GStreamer plugin for PulseAudio
ii  gstreamer0.10-schroedinger                1.0.5-1                              GStreamer plugin for encoding/decoding of Di
ii  gstreamer0.10-tools                       0.10.22-1                            Tools for use with GStreamer
ii  gstreamer0.10-x                           0.10.22-3                            GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0           0.10.22-3                            GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                        0.10.22-1                            Core GStreamer libraries and elements

```

---

### Post by kansasnoob on 2009-03-09
Plays OK for me. A thought though, I've added Crimsun's ppa:

[https://launchpad.net/~crimsun/+archive/ppa](https://launchpad.net/~crimsun/+archive/ppa)

Don't forget the GPG key.

That was originally discussed here:

[http://ubuntuforums.org/showthread.php?t=1084919](http://ubuntuforums.org/showthread.php?t=1084919)

---

### Post by yelo3 on 2009-03-09
No, those packages didn't solve my problems at all :(

---

