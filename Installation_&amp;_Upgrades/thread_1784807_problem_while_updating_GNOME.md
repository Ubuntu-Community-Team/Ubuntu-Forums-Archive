---
title: "problem while updating GNOME"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by cmwhidmore on 2011-06-17
So, a few days ago, I was updating a bunch of my packages. Everything was going smoothly until I hit a snag trying to get an update for GNOME:

```
root@MXX0200GTP-HP-PC:~# apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages
root@MXX0200GTP-HP-PC:~# 
```

Why is this happening? Normally, when one package needs a second package to install for it to work, apt-get gets that too.

And downloading swfdec-mozilla manually is not an option for me:
```
apt-get install swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  browser-plugin-gnash freepats gnash gnash-common gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-bad libass4 libavcodec52
  libavformat52 libavutil50 libboost-date-time1.42.0 libboost-thread1.42.0
  libcdaudio1 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0
  libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaad2 libfftw3-3
  libflite1 libgif4 libgme0 libgsm1 libgtkglext1 libiptcdata0 libkate1
  libmimic0 libmms0 libmodplug1 libmpcdec6 libofa0 liboil0.3 libopenspc0
  libpostproc51 librtmp0 libschroedinger-1.0-0 libsoundtouch1c2 libswscale0
  libts-0.0-0 libva1 libvpx0 libwildmidi0 libzbar0 tsconf
Suggested packages:
  libdvdcss2 debhelper fakeroot build-essential libfftw3-dev
The following NEW packages will be installed:
  browser-plugin-gnash freepats gnash gnash-common gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-bad libass4 libavcodec52
  libavformat52 libavutil50 libboost-date-time1.42.0 libboost-thread1.42.0
  libcdaudio1 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0
  libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaad2 libfftw3-3
  libflite1 libgif4 libgme0 libgsm1 libgtkglext1 libiptcdata0 libkate1
  libmimic0 libmms0 libmodplug1 libmpcdec6 libofa0 liboil0.3 libopenspc0
  libpostproc51 librtmp0 libschroedinger-1.0-0 libsoundtouch1c2 libswscale0
  libts-0.0-0 libva1 libvpx0 libwildmidi0 libzbar0 swfdec-mozilla tsconf
0 upgraded, 50 newly installed, 0 to remove and 250 not upgraded.
Need to get 59.9MB of archives.
After this operation, 100.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

Downloading the 59.9MB is not an attractive option - I am stuck with 56k dialup, and that would take three or four hours at the minimum... I just don't have that kind of time to devote to "hurry up and wait".

Any suggestions?

---

### Post by jerrrys on 2011-06-18
is this a possibility?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=bit+torrent+dial+up&sa=Search&cof=FORID:9#971](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=bit+torrent+dial+up&sa=Search&cof=FORID:9#971)

there are also package managers that will speed up download time.

---

