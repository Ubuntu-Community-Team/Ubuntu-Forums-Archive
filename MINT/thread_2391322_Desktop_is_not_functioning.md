---
title: "Desktop is not functioning"
date: 2018-05-08
forum: MINT
---

### Post by dolphinus12 on 2018-05-08
I am new to this forum so please tell me if I post something incorrectly so I can correct it ;)

OS: Linux Mint 18.3 (I hope this is the right forum to post on)

Yesterday I installed a number of routine updates and I noticed that the X.org server update was selected (with the update manager's recommended updates) so I installed it without thinking too hard. I then booted into windows for some gaming and when I booted back into Linux I just had a black screen, so, since it was late, I just shut the machine down for the night (I have been having some problems with the mouse hanging and was hoping it would heal itself). I booted the machine back up this morning but instead of the blue login screen I was greeted with a black screen and a cursor. Guessing that there was something wrong, I typed in my password and hit enter, which worked and it logged me in. When the desktop "loaded" all I had was a cursor (and discord started automatically). I eventually managed to get a terminal up and start firefox, system monitor, and synaptic to try to figure out what was wrong (which I still don't know but I'm guessing it was the x.org upgrade). So I am left with a black desktop that my mouse can interact with but I can't see.

I have tried killing and restarting plasma (basically just made windows leave "trails" on the screen as they were moved)
I have looked into forcing a downgrade on x.org but synaptic will only let me go back to a version older than the one I started with

Upgrades performed (according to synaptic) right before I started having problems
```
Commit Log for Mon May  7 18:41:41 2018


Upgraded the following packages:
avahi-autoipd (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
avahi-daemon (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
avahi-utils (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
cups-browsed (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
cups-filters (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
cups-filters-core-drivers (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
ffmpeg (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
firefox (59.0.1+linuxmint1+sylvia) to 59.0.2+linuxmint1+sylvia
firefox-locale-en (59.0.1+linuxmint1+sylvia) to 59.0.2+linuxmint1+sylvia
fwupd (0.8.3-0ubuntu2) to 0.8.3-0ubuntu3
ghostscript (9.18~dfsg~0-0ubuntu2.7) to 9.18~dfsg~0-0ubuntu2.8
ghostscript-x (9.18~dfsg~0-0ubuntu2.7) to 9.18~dfsg~0-0ubuntu2.8
gir1.2-ibus-1.0 (1.5.11-1ubuntu2) to 1.5.11-1ubuntu2.1
gir1.2-javascriptcoregtk-4.0 (2.18.6-0ubuntu0.16.04.1) to 2.20.1-0ubuntu0.16.04.1
gir1.2-webkit2-4.0 (2.18.6-0ubuntu0.16.04.1) to 2.20.1-0ubuntu0.16.04.1
hdparm (9.48+ds-1) to 9.48+ds-1ubuntu0.1
ibus-gtk:i386 (1.5.11-1ubuntu2) to 1.5.11-1ubuntu2.1
icu-devtools (55.1-7ubuntu0.3) to 55.1-7ubuntu0.4
ifupdown (0.8.10ubuntu1.2) to 0.8.10ubuntu1.3
initramfs-tools (0.122ubuntu8.10) to 0.122ubuntu8.11
initramfs-tools-bin (0.122ubuntu8.10) to 0.122ubuntu8.11
initramfs-tools-core (0.122ubuntu8.10) to 0.122ubuntu8.11
libav-tools (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavahi-client3 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-client3:i386 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-common-data (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-common-data:i386 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-common3 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-common3:i386 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-core7 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-glib1 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavahi-gobject0 (0.6.32~rc+dfsg-1ubuntu2) to 0.6.32~rc+dfsg-1ubuntu2.2
libavcodec-dev (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavcodec-extra (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavcodec-ffmpeg-extra56 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavdevice-ffmpeg56 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavfilter-ffmpeg5 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavformat-dev (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavformat-ffmpeg56 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavresample-ffmpeg2 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavutil-dev (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libavutil-ffmpeg54 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libcupsfilters1 (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
libcupsfilters1:i386 (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
libdfu1 (0.8.3-0ubuntu2) to 0.8.3-0ubuntu3
libfontembed1 (1.8.3-2ubuntu3.1) to 1.8.3-2ubuntu3.4
libfwupd1 (0.8.3-0ubuntu2) to 0.8.3-0ubuntu3
libgs9 (9.18~dfsg~0-0ubuntu2.7) to 9.18~dfsg~0-0ubuntu2.8
libgs9-common (9.18~dfsg~0-0ubuntu2.7) to 9.18~dfsg~0-0ubuntu2.8
libibus-1.0-5 (1.5.11-1ubuntu2) to 1.5.11-1ubuntu2.1
libibus-1.0-5:i386 (1.5.11-1ubuntu2) to 1.5.11-1ubuntu2.1
libicu-dev (55.1-7ubuntu0.3) to 55.1-7ubuntu0.4
libicu55 (55.1-7ubuntu0.3) to 55.1-7ubuntu0.4
libicu55:i386 (55.1-7ubuntu0.3) to 55.1-7ubuntu0.4
libjavascriptcoregtk-4.0-18 (2.18.6-0ubuntu0.16.04.1) to 2.20.1-0ubuntu0.16.04.1
libmysqlclient-dev (5.7.21-0ubuntu0.16.04.1) to 5.7.22-0ubuntu0.16.04.1
libmysqlclient20 (5.7.21-0ubuntu0.16.04.1) to 5.7.22-0ubuntu0.16.04.1
libpam-modules (1.1.8-3.2ubuntu2) to 1.1.8-3.2ubuntu2.1
libpam-modules-bin (1.1.8-3.2ubuntu2) to 1.1.8-3.2ubuntu2.1
libpam-runtime (1.1.8-3.2ubuntu2) to 1.1.8-3.2ubuntu2.1
libpam0g (1.1.8-3.2ubuntu2) to 1.1.8-3.2ubuntu2.1
libpci3 (1:3.3.1-1.1ubuntu1.1) to 1:3.3.1-1.1ubuntu1.2
libperl5.22 (5.22.1-9ubuntu0.2) to 5.22.1-9ubuntu0.3
libpostproc-ffmpeg53 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libpulse-dev (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulse-mainloop-glib0 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulse-mainloop-glib0:i386 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulse0 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulse0:i386 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulsedsp (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libpulsedsp:i386 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
libraw15 (0.17.1-1ubuntu0.1) to 0.17.1-1ubuntu0.2
libruby2.3 (2.3.1-2~16.04.6) to 2.3.1-2~16.04.9
libsdl-image1.2 (1.2.12-5build2) to 1.2.12-5+deb9u1build0.16.04.1
libsdl-image1.2:i386 (1.2.12-5build2) to 1.2.12-5+deb9u1build0.16.04.1
libsdl2-image-2.0-0 (2.0.1+dfsg-2) to 2.0.1+dfsg-2+deb9u1build0.16.04.1
libssl-dev (1.0.2g-1ubuntu4.10) to 1.0.2g-1ubuntu4.12
libssl1.0.0 (1.0.2g-1ubuntu4.10) to 1.0.2g-1ubuntu4.12
libssl1.0.0:i386 (1.0.2g-1ubuntu4.10) to 1.0.2g-1ubuntu4.12
libswresample-dev (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libswresample-ffmpeg1 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libswscale-dev (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libswscale-ffmpeg3 (7:2.8.11-0ubuntu0.16.04.1) to 7:2.8.14-0ubuntu0.16.04.1
libvncclient1 (0.9.10+dfsg-3ubuntu0.16.04.1) to 0.9.10+dfsg-3ubuntu0.16.04.2
libwayland-bin (1.12.0-1~ubuntu16.04.2) to 1.12.0-1~ubuntu16.04.3
libwayland-client0 (1.12.0-1~ubuntu16.04.2) to 1.12.0-1~ubuntu16.04.3
libwayland-cursor0 (1.12.0-1~ubuntu16.04.2) to 1.12.0-1~ubuntu16.04.3
libwayland-dev (1.12.0-1~ubuntu16.04.2) to 1.12.0-1~ubuntu16.04.3
libwayland-server0 (1.12.0-1~ubuntu16.04.2) to 1.12.0-1~ubuntu16.04.3
libwebkit2gtk-4.0-37 (2.18.6-0ubuntu0.16.04.1) to 2.20.1-0ubuntu0.16.04.1
lshw (02.17-1.1ubuntu3.4) to 02.17-1.1ubuntu3.5
mysql-client-core-5.7 (5.7.21-0ubuntu0.16.04.1) to 5.7.22-0ubuntu0.16.04.1
mysql-common (5.7.21-0ubuntu0.16.04.1) to 5.7.22-0ubuntu0.16.04.1
mysql-server-core-5.7 (5.7.21-0ubuntu0.16.04.1) to 5.7.22-0ubuntu0.16.04.1
openjdk-8-jre (8u151-b12-0ubuntu0.16.04.2) to 8u162-b12-0ubuntu0.16.04.2
openjdk-8-jre-headless (8u151-b12-0ubuntu0.16.04.2) to 8u162-b12-0ubuntu0.16.04.2
openrazer-daemon (2.2.2~ubuntu16.04.1) to 2.3.0~ubuntu16.04.1
openrazer-doc (2.2.2~ubuntu16.04.1) to 2.3.0~ubuntu16.04.1
openrazer-kernel-modules-dkms (2.2.2~ubuntu16.04.1) to 2.3.0~ubuntu16.04.1
openrazer-meta (2.2.2~ubuntu16.04.1) to 2.3.0~ubuntu16.04.1
openssl (1.0.2g-1ubuntu4.10) to 1.0.2g-1ubuntu4.12
oracle-java8-installer (8u161-1~webupd8~0) to 8u171-1~webupd8~0
oracle-java8-set-default (8u161-1~webupd8~0) to 8u171-1~webupd8~0
patch (2.7.5-1) to 2.7.5-1ubuntu0.16.04.1
pciutils (1:3.3.1-1.1ubuntu1.1) to 1:3.3.1-1.1ubuntu1.2
perl (5.22.1-9ubuntu0.2) to 5.22.1-9ubuntu0.3
perl-base (5.22.1-9ubuntu0.2) to 5.22.1-9ubuntu0.3
perl-modules-5.22 (5.22.1-9ubuntu0.2) to 5.22.1-9ubuntu0.3
polychromatic (0.3.11.2.1-bionic) to 0.3.12-xenial1
pulseaudio (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
pulseaudio-module-bluetooth (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
pulseaudio-module-x11 (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
pulseaudio-utils (1:8.0-0ubuntu3.8) to 1:8.0-0ubuntu3.10
python-crypto (2.6.1-6ubuntu0.16.04.2) to 2.6.1-6ubuntu0.16.04.3
python3-crypto (2.6.1-6ubuntu0.16.04.2) to 2.6.1-6ubuntu0.16.04.3
python3-openrazer (2.2.2~ubuntu16.04.1) to 2.3.0~ubuntu16.04.1
python3-problem-report (2.20.1-0ubuntu2.15) to 2.20.1-0ubuntu2.16
qpdf (6.0.0-2) to 8.0.2-3~16.04.1
ruby2.3 (2.3.1-2~16.04.6) to 2.3.1-2~16.04.9
virtualbox-5.2 (5.2.8-121009~Ubuntu~xenial) to 5.2.10-122088~Ubuntu~xenial
xdg-user-dirs (0.15-2ubuntu6) to 0.15-2ubuntu6.16.04.1
xserver-common (2:1.18.4-0ubuntu0.2) to 2:1.18.4-0ubuntu0.7
xserver-xorg-core (2:1.18.4-0ubuntu0.2) to 2:1.18.4-0ubuntu0.7

Installed the following packages:
libqpdf21 (8.0.2-3~16.04.1)
```

If anybody needs any additional information about this I would be happy to provide it.
Thanks!
dolphinus12

---

### Post by Frogs Hair on 2018-05-08
Moved to *Other OS/Mint.*

---

