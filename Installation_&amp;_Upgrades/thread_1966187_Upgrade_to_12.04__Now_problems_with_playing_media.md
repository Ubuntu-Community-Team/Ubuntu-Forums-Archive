---
title: "Upgrade to 12.04  Now problems with playing media"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by iraiam on 2012-04-26
HI, I upgraded to 12.04 and now my ability to play CD DVD is hosed!  could not get anything at all until I did "sudo apt-get remove libdvdread4"  THEN "sudo apt-get install libdvdread4"

Now I can get one step farther but I get the following error(s) when trying to play a DVD, I can't install these packages,  trying to install them with apt-get says they are already the latest version.
**********************************************************************
The following packages have unmet dependencies:

gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed

***********************************************************************

Anyone have any ideas?,  I am not sure what to do next.

Thanks Much

---

### Post by dFlyer on 2012-04-26
Have you installed ubuntu-restricted-extras?

---

### Post by iraiam on 2012-04-26
> **dFlyer said:**
> Have you installed ubuntu-restricted-extras?


Yes, I tried but got this response.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 libsoundtouch0 libts-0.0-0 libmodplug1 libtwolame0 libzbar0
  libgraphicsmagick3 libzvbi-common libflite1 libxine1-x libbluray1 libsvga1
  libzvbi0 libxcb-xv0 libdca0 libiso9660-8 libfftw3-3 libslv2-9
  libdirectfb-1.2-9 libaacs0 libgme0 libspandsp2 freepats liba52-0.7.4
  libxine1-console libwildmidi1 libdc1394-22 libkate1 libcdaudio1 libmimic0
  libsidplay1 libwildmidi-config tsconf libcelt0-0
  libgstreamer-plugins-bad0.10-0 libvcdinfo0 libmpcdec6 libofa0 libmpeg2-4
  libmms0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ira@MediaCenter:~$

---

### Post by iraiam on 2012-04-26
Also there is a window that opens up before these errors that says it's Python (V2.7) that requires these packages for DVD playback.

It is a media center computer so I'm just going to boot to my 11.10 partition until this gets resolved. It appears I'm not the only one having this problem.

---

### Post by techsupport on 2012-04-26
> **iraiam said:**
> HI, I upgraded to 12.04 and now my ability to play CD DVD is hosed!  could not get anything at all until I did "sudo apt-get remove libdvdread4"  THEN "sudo apt-get install libdvdread4"

Did you go step by step installing your media codecs from this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Make sure you get those also installed, because I think you missed something.

---

### Post by iraiam on 2012-04-27
> **techsupport said:**
> Did you go step by step installing your media codecs from this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Make sure you get those also installed, because I think you missed something.


Thanks, that got some of it,  I can play media now, DVD playback locks up sometimes, that's not something I have seen before.

Some other media players still don't function but it's at least usable now.

---

### Post by techsupport on 2012-04-27
> **iraiam said:**
> Thanks, that got some of it,  I can play media now, DVD playback locks up sometimes, that's not something I have seen before.

Some other media players still don't function but it's at least usable now.

It might actually be better for you to do a fresh install and then go down that guide list step by step..  I just tested it, and everything works once you follow the guide.  Try it. Fastest way to be sure.

---

