---
title: "Pulseaudio version 12 install-upgrade"
date: 2018-06-24
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2018-06-24
Pulseaudio verison 12 came out and my 16.04.4 is stil using version 8, I want to know how to update my Pulseaudio to version 12.  I understand that it fixes-corrects many bugs and problems.  

I am waiting until July to upgrade from 16.04.4 to 18.04.1.  What version does 18.04 have?

---

### Post by linux4me on 2018-06-24
This is what I get on my up-to-date 18.04 installation:
```

dpkg --list | grep pulseaudio
ii  gstreamer1.0-pulseaudio:amd64              1.14.0-1ubuntu1                        amd64        GStreamer plugin for PulseAudio
ii  pulseaudio                                 1:11.1-1ubuntu7.1                      amd64        PulseAudio sound server
ii  pulseaudio-module-bluetooth                1:11.1-1ubuntu7.1                      amd64        Bluetooth module for PulseAudio sound server
ii  pulseaudio-utils                           1:11.1-1ubuntu7.1                      amd64        Command line tools for the PulseAudio sound server

```

---

### Post by jlh68 on 2018-06-24
Thanks. This is what I have. It looks like you have version 11.  Version 12 was released on June 20th.

dpkg --list | grep pulseaudio
ii  gstreamer1.0-pulseaudio:amd64      1.8.3-1ubuntu0.4            amd64        GStreamer plugin for PulseAudio
ii  projectm-pulseaudio                           2.1.0+dfsg-3build1         amd64        projectM PulseAudio module
ii  pulseaudio                                           1:8.0-0ubuntu3.10          amd64        PulseAudio sound server
ii  pulseaudio-module-bluetooth            1:8.0-0ubuntu3.10         amd64        Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-x11                      1:8.0-0ubuntu3.10         amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                                   1:8.0-0ubuntu3.10         amd64        Command line tools for the PulseAudio sound server

---

