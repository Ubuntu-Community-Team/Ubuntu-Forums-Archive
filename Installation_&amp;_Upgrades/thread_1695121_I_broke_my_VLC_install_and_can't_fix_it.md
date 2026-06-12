---
title: "I broke my VLC install and can't fix it"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by swiftdr on 2011-02-25
I screwed up my VLC install and can't fix it. I installed a new repo to get an updated version of Evolution Mail and hit "Mark All Upgrades" and it broke my VLC. I can't figure out how to undo the damage. It can't install vlc-nox for some reason. Is there a simple way to undo this?

This is the repo I added:
[http://ppa.launchpad.net/suraia/ppa/ubuntu](http://ppa.launchpad.net/suraia/ppa/ubuntu) maverick main

This is the text from my history:

```
Commit Log for Fri Feb 25 02:48:00 2011


Removed the following packages:
gir1.0-glib-2.0
libgirepository1.0-1
vlc
vlc-nox
vlc-plugin-notify
vlc-plugin-pulse

Upgraded the following packages:
evolution (2.30.3-1ubuntu7.3) to 2.32.2-0ubuntu1~maverick1
evolution-common (2.30.3-1ubuntu7.3) to 2.32.2-0ubuntu1~maverick1
evolution-couchdb (0.5.0-0ubuntu1) to 0.5.1-0ubuntu1~maverick1
evolution-data-server (2.30.3-2ubuntu2.1) to 2.32.2-0ubuntu1~maverick1
evolution-data-server-common (2.30.3-2ubuntu2.1) to 2.32.2-0ubuntu1~maverick1
evolution-exchange (2.30.3-0ubuntu2) to 2.32.2-0ubuntu2~maverick1
evolution-indicator (0.2.10-0ubuntu1) to 0.2.12-0ubuntu1~maverick1
evolution-plugins (2.30.3-1ubuntu7.3) to 2.32.2-0ubuntu1~maverick1
evolution-webcal (2.28.1-1) to 2.32.0-0ubuntu2~maverick1
jockey-common (0.5.10-0ubuntu5.2) to 0.7.1-0ubuntu1~maverick1
jockey-gtk (0.5.10-0ubuntu5.2) to 0.7.1-0ubuntu1~maverick1
libcairo2 (1.10.0-1ubuntu3) to 1.10.2-2ubuntu1~maverick1
libdrm-intel1 (2.4.21-1ubuntu2.1) to 2.4.23-1ubuntu3~maverick2
libdrm-nouveau1 (2.4.21-1ubuntu2.1) to 2.4.23-1ubuntu3~maverick2
libdrm-radeon1 (2.4.21-1ubuntu2.1) to 2.4.23-1ubuntu3~maverick2
libdrm2 (2.4.21-1ubuntu2.1) to 2.4.23-1ubuntu3~maverick2
libebackend1.2-0 (2.30.3-2ubuntu2.1) to 2.32.2-0ubuntu1~maverick1
libegroupwise1.2-13 (2.30.3-2ubuntu2.1) to 2.32.2-0ubuntu1~maverick1
libevolution (2.30.3-1ubuntu7.3) to 2.32.2-0ubuntu1~maverick1
libgadu3 (1:1.9.0~rc2-1) to 1:1.9.0-2~maverick1
libgl1-mesa-dri (7.9~git20100924-0ubuntu2) to 7.10-1ubuntu3~maverick1
libgl1-mesa-glx (7.9~git20100924-0ubuntu2) to 7.10-1ubuntu3~maverick1
libglu1-mesa (7.9~git20100924-0ubuntu2) to 7.10-1ubuntu3~maverick1
libgtkhtml-editor-common (1:3.30.3-1ubuntu1) to 1:3.32.2-0ubuntu1~maverick1
libgtkhtml-editor0 (1:3.30.3-1ubuntu1) to 1:3.32.2-0ubuntu1~maverick1
libgtkhtml3.14-19 (1:3.30.3-1ubuntu1) to 1:3.32.2-0ubuntu1~maverick1
libplymouth2 (0.8.2-2ubuntu5.1) to 0.8.2-2ubuntu5.2suraia1~maverick2
libpulse-browse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
libpulse-mainloop-glib0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
libpulse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
libpurple-bin (1:2.7.3-1ubuntu3.2) to 1:2.7.9-1ubuntu1~maverick1
libpurple0 (1:2.7.3-1ubuntu3.2) to 1:2.7.9-1ubuntu1~maverick1
libsoup-gnome2.4-1 (2.31.92-0ubuntu1) to 2.32.2-2~maverick2
libsoup2.4-1 (2.31.92-0ubuntu1) to 2.32.2-2~maverick2
libsqlite3-0 (3.7.2-1ubuntu0.1) to 3.7.4-2~maverick1
libva-x11-1 (1.0.1-3) to 1.0.8-3~maverick1
libva1 (1.0.1-3) to 1.0.8-3~maverick1
light-themes (0.1.8.3) to 0.1.8.4suraia2~maverick3
linux-generic (2.6.35.25.32) to 2.6.38.5.19~maverick1
linux-headers-generic (2.6.35.25.32) to 2.6.38.5.19~maverick1
linux-image-generic (2.6.35.25.32) to 2.6.38.5.19~maverick1
linux-libc-dev (2.6.35-1025.44) to 2.6.38-5.32~maverick1
plymouth (0.8.2-2ubuntu5.1) to 0.8.2-2ubuntu5.2suraia1~maverick2
plymouth-label (0.8.2-2ubuntu5.1) to 0.8.2-2ubuntu5.2suraia1~maverick2
plymouth-theme-ubuntu-logo (0.8.2-2ubuntu5.1) to 0.8.2-2ubuntu5.2suraia1~maverick2
plymouth-theme-ubuntu-text (0.8.2-2ubuntu5.1) to 0.8.2-2ubuntu5.2suraia1~maverick2
pulseaudio (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
pulseaudio-esound-compat (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
pulseaudio-module-bluetooth (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
pulseaudio-module-gconf (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
pulseaudio-module-x11 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
pulseaudio-utils (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) to 1:0.9.22+stable-queue-24-g67d18-0ubuntu1~maverick1
python-gobject (2.21.5-0ubuntu3) to 2.21.5-0ubuntu3suraia1~maverick2
python-gobject-cairo (2.21.5-0ubuntu3) to 2.21.5-0ubuntu3suraia1~maverick2
transmission-common (2.04-0ubuntu2) to 2.13-0ubuntu3~maverick1
transmission-gtk (2.04-0ubuntu2) to 2.13-0ubuntu3~maverick1
ttf-liberation (1.05.2.20091019-4) to 1.06.0.20100721-0suraia1~maverick1
vim-common (2:7.2.330-1ubuntu4) to 2:7.3.035+hg~8fdc12103333-1ubuntu1~maverick1
vim-tiny (2:7.2.330-1ubuntu4) to 2:7.3.035+hg~8fdc12103333-1ubuntu1~maverick1
xserver-xorg-video-intel (2:2.12.0-1ubuntu5.1) to 2:2.14.0-1ubuntu9~maverick1
xserver-xorg-video-nouveau (1:0.0.16+git20100805+b96170a-0ubuntu1) to 1:0.0.16+git20110107+b795ca6e-0ubuntu1~maverick1

Installed the following packages:
gir1.2-glib-2.0 (0.10.0-0ubuntu3~maverick1)
libcamel1.2-19 (2.32.2-0ubuntu1~maverick1)
libdrm-nouveau1a (2.4.23-1ubuntu3~maverick2)
libebook1.2-10 (2.32.2-0ubuntu1~maverick1)
libecal1.2-8 (2.32.2-0ubuntu1~maverick1)
libedata-book1.2-8 (2.32.2-0ubuntu1~maverick1)
libedata-cal1.2-10 (2.32.2-0ubuntu1~maverick1)
libedataserver1.2-14 (2.32.2-0ubuntu1~maverick1)
libedataserverui1.2-11 (2.32.2-0ubuntu1~maverick1)
libegl1-mesa (7.10-1ubuntu3~maverick1)
libegl1-mesa-drivers (7.10-1ubuntu3~maverick1)
libgirepository-1.0-1 (0.10.0-0ubuntu3~maverick1)
libxcb-shape0 (1.6-1)
libxcb-xfixes0 (1.6-1)
linux-headers-2.6.38-5 (2.6.38-5.32~maverick1)
linux-headers-2.6.38-5-generic (2.6.38-5.32~maverick1)
linux-image-2.6.38-5-generic (2.6.38-5.32~maverick1)

```

---

### Post by lifelike27 on 2011-06-10
Have you tried purging the install files first and then re-installing VLC?
```
sudo apt-get purge vlc vlc-plugin-pulse mozilla-plugin-vlc
```

Followed by:
```
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```

---

