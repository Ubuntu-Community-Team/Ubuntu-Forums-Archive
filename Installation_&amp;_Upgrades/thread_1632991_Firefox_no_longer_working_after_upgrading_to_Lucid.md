---
title: "Firefox no longer working after upgrading to Lucid Lynx"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by MYJC on 2010-11-28
I got an error during the upgrade but chose to let the upgrade complete. Now my Firefox won't lauch. I tried uninstalling and reinstalling it from the Terminal and got the following:

> rick@Desktop:~$ sudo apt-get install firefox
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 ispell ibritish libwxbase2.6-0 libmtp7 libopenal0a libusplash0
  libvolume-id0 python2.5-examples libpolkit-dbus2 libneon27 libavutil1d
  libexpat1-dev libpt-1.10.10-plugins-alsa python-4suite-xml libxklavier12
  libgucharmap6 libgtkhtml3.16-cil libpthread-stubs0 libicu38
  libservlet2.4-java python-launchpad-bugs sqlite xulrunner-1.9
  libpolkit-gnome0 libbeagle1 policykit-gnome libswscale1d libnm-util0
  libmagick10 libdns35 x11proto-render-dev libggzmod4 libqt4-core libiso9660-5
  libsgutils1 libx11-xcb1 libsmbios1 libfontconfig1-dev libtrackerclient0
  libgpod3 python2.5 x11proto-kb-dev libisccc30 libtracker-gtk0
  libdirectfb-1.0-0 libcdio7 libavcodec1d policykit libxosd2 xtrans-dev
  libx264-57 libalut0 libavahi-core5 libhesiod0 acl libffi4 x11proto-input-dev
  dhcdbd compiz-fusion-plugins-extra liblwres30 bluez-audio mplayer-skins
  libqt4-gui libwxgtk2.6-0 openoffice.org-hyphenation-en-us python-sexy
  libnm-glib0 libggz2 libpoppler2 libpolkit-grant2 libntfs-3g23 libbind9-30
  ubuntu-gdm-themes libpoppler-glib2 zlib1g-dev libpostproc1d
  libswt3.2-gtk-java libwvstreams4.4-extras libswfdec-0.6-90 openssl-blacklist
  libfreetype6-dev libpt-1.10.10 libdbus-qt-1-1c2 libxau-dev libopal-2.2
  libflickrnet2.1.5-cil libdvdread3 libzip1 libhunspell-1.1-0
  libtotem-plparser10 libiw29 libdc1394-13 libavformat1d libopenexr2ldbl
  openoffice.org-writer2latex libgnome-speech7 libisccfg30 libcamel1.2-11
  libxrender-dev libbeecrypt6 libpq5 libavahi-compat-libdnssd1
  libmjpegtools0c2a libggzcore9 libzephyr3 libxft-dev libx11-dev python-gdata
  odt2txt openoffice.org-thesaurus-en-au libwvstreams4.4-base libisc35 sqlite3
  libxcb1-dev libimlib2 iamerican libaudit0 libnss3-0d x11proto-core-dev
  libswt3.2-gtk-jni libcucul0 libxdmcp-dev openoffice.org-hyphenation
  libpthread-stubs0-dev libseda-java o3read libpolkit2 hwtest libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.12+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Rubi1200 on 2010-11-29
Hi and welcome to the forums :)

From the terminal try these commands:

```
sudo apt-get install -f

```
```
sudo dpkg --configure -a
```

---

