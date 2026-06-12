---
title: "apt-get upgrade not completing"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by paul_whan on 2006-05-13
I am having trouble upgrading these files:

  gstreamer0.8-alsa gstreamer0.8-audiofile gstreamer0.8-cdparanoia
  gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-flac
  gstreamer0.8-gnomevfs gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jpeg
  gstreamer0.8-misc gstreamer0.8-musepack gstreamer0.8-oss
  gstreamer0.8-plugin-apps gstreamer0.8-sdl gstreamer0.8-speex
  gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x
  ifrename libgnutls11 libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libmysqlclient14 libneon24 libopenal0 libreadline4
  python-gst xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro xserver-xorg-input-fpit
  xserver-xorg-input-hyperpen xserver-xorg-input-magellan
  xserver-xorg-input-microtouch xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void

i used apt-get upgrade and those files that displayed. would some please give me some advice of what to do here?

---

### Post by ash211 on 2006-05-13
Instead of running ```
sudo apt-get upgrade
```type```
sudo apt-get dist-upgrade
```  Dist-upgrading is usually able to install these packages that are otherwise 'held back'.

---

