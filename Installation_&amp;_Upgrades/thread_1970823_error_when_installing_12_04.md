---
title: "error when installing 12 04"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by spud1 on 2012-05-01
i tried to install 12 04 and i freaked out in the middle of installing  so in recovery mode I tried **apt-get dist-upgrade**
 but i get this error

[B]dpkg: error: parsing file '/var/lib/dpkg/available' near line 44967 package 'lxbaacs':

blank line in value of field 'description'

e: sub-process /usr/bin/dpkg returned an error code (2)[/B]

how do i fixed it

---

### Post by darkod on 2012-05-01
Are you saying that you interrupted the install before it finished?

---

### Post by spud1 on 2012-05-01
no i got errors saying this program installed and configure....there were a lot of them. all i have now is the desktop no side bar or clock or icon to shutdown

---

### Post by darkod on 2012-05-01
> **spud1 said:**
> i tried to install 12 04 and i freaked out in the middle of installing 

The above sounds like you started installing and interrupted it.

Did you actually try upgrading to 12.04, not installing from scratch?

If we are talking about upgrading, not installing, try booting into recovery mode again and at the root prompt do:
dpkg --configure -a

See how that goes.

---

### Post by spud1 on 2012-05-01
I got errors when I tried it

---

### Post by darkod on 2012-05-01
Can you be more specific please?

Many errors or just few of them saying the system is read only or similar?

---

### Post by spud1 on 2012-05-01
many errors...looks like a list of programs......it would be easier if I can run terminal in desktop

---

### Post by spud1 on 2012-05-01
found out to open a term....it says




spud@spud-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of compiz-plugins-default:
 compiz-plugins-default depends on libdecoration0 (= 1:0.9.7.6-0ubuntu1); however:
  Version of libdecoration0 on system is 1:0.9.6+bzr20110929-0ubuntu6.1.
dpkg: error processing compiz-plugins-default (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libglew1.6 (>= 1.6.0); however:
  Package libglew1.6 is not installed.
 unity depends on libnux-2.0-0; however:
  Package libnux-2.0-0 is not installed.
 unity depends on libunity-core-5.0-5 (= 5.10.0-0ubuntu6); however:
  Package libunity-core-5.0-5 is not installed.
 unity depends on libxfixes3 (>= 1:5.0-4ubuntu1); however:
  Version of libxfixes3 on system is 1:5.0-4.
 unity depends on unity-common (= 5.10.0-0ubuntu6); however:
  Version of unity-common on system is 4.28.0-0ubuntu2.
 unity depends on libnux-abiversion-20120411.01; however:
  Package libnux-abiversion-20120411.01 is not installed.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on libxatracker1; however:
  Package libxatracker1 is not installed.
dpkg: error processing xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins:
 compiz-plugins depends on compiz-plugins-default (= 1:0.9.7.6-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.
dpkg: error processing compiz-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ffmpeg:
 ffmpeg depends on libav-tools; however:
  Package libav-tools is not installed.
dpkg: error processing ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-core:
 compiz-core depends on libglibmm-2.4-1c2a (>= 2.32.0); however:
  Version of libglibmm-2.4-1c2a on system is 2.30.0-0ubuntu1.
dpkg: error processing compiz-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-extra:
 compiz-plugins-extra depends on compiz-core; however:
  Package compiz-core is not configured yet.
 compiz-plugins-extra depends on compiz-core-abiversion-20120305; however:
  Package compiz-core-abiversion-20120305 is not installed.
  Package compiz-core which provides compiz-core-abiversion-20120305 is not configured yet.
dpkg: error processing compiz-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libswscale2:
 libswscale2 depends on libavutil51 (>= 4:0.8.1-0ubuntu1) | libavutil-extra-51 (>= 4:0.8.1); however:
  Package libavutil51 is not installed.
  Version of libavutil-extra-51 on system is 4:0.7.3ubuntu0.11.10.1.
dpkg: error processing libswscale2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-main:
 compiz-plugins-main depends on compiz-core; however:
  Package compiz-core is not configured yet.
 compiz-plugins-main depends on compiz-core-abiversion-20120305; however:
  Package compiz-core-abiversion-20120305 is not installed.
  Package compiz-core which provides compiz-core-abiversion-20120305 is not configured yet.
dpkg: error processing compiz-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcompizconfig0:
 libcompizconfig0 depends on compiz-core; however:
  Package compiz-core is not configured yet.
 libcompizconfig0 depends on compiz-core-abiversion-20120305; however:
  Package compiz-core-abiversion-20120305 is not installed.
  Package compiz-core which provides compiz-core-abiversion-20120305 is not configured yet.
dpkg: error processing libcompizconfig0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavfilter2:
 libavfilter2 depends on libavcodec53 (>= 4:0.8.1-0ubuntu1) | libavcodec-extra-53 (>= 4:0.8.1); however:
  Package libavcodec53 is not installed.
  Version of libavcodec-extra-53 on system is 4:0.7.3ubuntu0.11.10.1.
 libavfilter2 depends on libavformat53 (>= 4:0.8.1-0ubuntu1) | libavformat-extra-53 (>= 4:0.8.1); however:
  Version of libavformat53 on system is 4:0.7.3-0ubuntu0.11.10.1.
  Package libavformat-extra-53 is not installed.
 libavfilter2 depends on libavutil51 (>= 4:0.8.1-0ubuntu1) | libavutil-extra-51 (>= 4:0.8.1); however:
  Package libavutil51 is not installed.
  Version of libavutil-extra-51 on system is 4:0.7.3ubuntu0.11.10.1.
 libavfilter2 depends on libswscale2 (>= 4:0.8.1-0ubuntu1) | libswscale-extra-2 (>= 4:0.8.1); however:
  Package libswscale2 is not configured yet.
  Package libswscale-extra-2 is not installed.
 libavfilter2 depends on libswscale2 (<< 4:0.8.1-99) | libswscale-extra-2 (<< 4:0.8.1.99); however:
  Package libswscale2 is not configured yet.
  Package libswscale-extra-2 is not installed.
dpkg: error processing libavfilter2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpostproc52:
 libpostproc52 depends on libavutil51 (>= 4:0.8.1-0ubuntu1) | libavutil-extra-51 (>= 4:0.8.1); however:
  Package libavutil51 is not installed.
  Version of libavutil-extra-51 on system is 4:0.7.3ubuntu0.11.10.1.
dpkg: error processing libpostproc52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libdecoration0 (>= 1:0.9.7.0~bzr2995-0ubuntu1~ppa1); however:
  Version of libdecoration0 on system is 1:0.9.6+bzr20110929-0ubuntu6.1.
 compiz-gnome depends on compiz-plugins-default (= 1:0.9.7.6-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-main-default:
 compiz-plugins-main-default depends on compiz-core; however:
  Package compiz-core is not configured yet.
 compiz-plugins-main-default depends on compiz-core-abiversion-20120305; however:
  Package compiz-core-abiversion-20120305 is not installed.
  Package compiz-core which provides compiz-core-abiversion-20120305 is not configured yet.
dpkg: error processing compiz-plugins-main-default (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz-plugins-default
 unity
 xserver-xorg-video-vmware
 compiz-plugins
 ffmpeg
 compiz-core
 compiz-plugins-extra
 libswscale2
 compiz-plugins-main
 libcompizconfig0
 libavfilter2
 libpostproc52
 compiz-gnome
 compiz-plugins-main-default

---

### Post by darkod on 2012-05-01
Sorry, unfortunately I don't know anything about these errors. Maybe someone else will jump in.

---

### Post by spud1 on 2012-05-02
can someone else help me

---

