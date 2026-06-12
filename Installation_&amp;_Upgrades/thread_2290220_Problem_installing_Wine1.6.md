---
title: "Problem installing Wine1.6"
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by raja-srijan on 2015-08-10
Hi all,

I've Ubuntu 14.04 installed and I'm trying to install wine on my system, but i get the following error:

```
sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dbus : Depends: upstart (>= 0.6.3-6)
        Recommends: libpam-systemd but it is not going to be installed
 default-jre : Depends: openjdk-8-jre (>= 8~b132-1) but it is not going to be installed
 default-jre-headless : Depends: openjdk-8-jre-headless (>= 8~b132-1) but it is not going to be installed
 gconf-service : Depends: gconf-service-backend (= 3.2.6-0ubuntu2) but it is not going to be installed
 gdb : Depends: libpython3.4 (>= 3.4~b1) but it is not going to be installed
 gir1.2-peas-1.0 : Depends: libpeas-1.0-0 (>= 1.6.2) but it is not going to be installed
 gitk : Depends: git (> 1:1.9.1)
        Depends: git (< 1:1.9.1-.)
 gstreamer1.0-plugins-good : Depends: libsoup2.4-1 (>= 2.38) but it is not going to be installed
 libaccounts-qt5-1 : Depends: libaccounts-glib0 (>= 1.14) but it is not going to be installed
 libgl1-mesa-glx : Depends: libglapi-mesa (= 10.1.3-0ubuntu0.4)
                   Recommends: libgl1-mesa-dri (>= 7.2)
 libgnome2-0 : Depends: libgnome2-common (>= 2.32) but it is not going to be installed
               Depends: libgnome2-common (< 2.33) but it is not going to be installed
               Depends: libgnome2-bin
               Recommends: gvfs but it is not going to be installed
 libgnomevfs2-0 : Depends: libgnomevfs2-common (>= 1:2.24)
                  Depends: libgnomevfs2-common (< 1:2.25)
                  Recommends: dbus-x11
 libnm-glib4 : Depends: libgudev-1.0-0 (>= 146) but it is not going to be installed
 libnm-util2 : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                        libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 liboauth0 : Depends: libcurl3-gnutls (>= 7.16.2) but it is not going to be installed
             Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                      libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 libpython3-dev : Depends: libpython3.4-dev (>= 3.4.0-0~) but it is not going to be installed
 libpython3-stdlib : Depends: libpython3.4-stdlib (>= 3.4.0-0~) but it is not going to be installed
 libqt5gui5 : Depends: libgles2-mesa (>= 7.8.1) or
                       libgles2
 librasqal3 : Depends: libraptor2-0 (>= 2.0.12) but it is not going to be installed
 librdf0 : Depends: libraptor2-0 (>= 2.0.12) but it is not going to be installed
 libthumbnailer0 : Depends: libsoup2.4-1 (>= 2.4.0) but it is not going to be installed
 libubuntu-application-api-mirserver1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140408.1) but it is not going to be installed
 libudev1 : Breaks: libudev1:i386 (!= 204-5ubuntu20.13) but 204-5ubuntu20.12 is to be installed
 libudev1:i386 : Breaks: libudev1 (!= 204-5ubuntu20.12) but 204-5ubuntu20.13 is to be installed
 libunity-core-6.0-9 : Depends: libnux-4.0-0 but it is not going to be installed
 libunity-mir1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140411) but it is not going to be installed
 python3-aptdaemon.pkcompat : Depends: gir1.2-packagekitglib-1.0 (>= 0.8.9) but it is not going to be installed
 python3-software-properties : Depends: python3-pycurl but it is not going to be installed
 python3.4 : Depends: libpython3.4-stdlib (= 3.4.0-2ubuntu1.1) but it is not going to be installed
 qtdeclarative5-qtmultimedia-plugin : Depends: libqt5multimedia5-plugins but it is not going to be installed
 qtdeclarative5-ubuntu-ui-toolkit-plugin : Depends: libqt5svg5 but it is not going to be installed
                                           Depends: qtdeclarative5-window-plugin but it is not going to be installed
 signon-plugin-password : Depends: signond but it is not going to be installed
 upower : Depends: libgudev-1.0-0 (>= 146) but it is not going to be installed
          Depends: libimobiledevice4 (>= 0.9.7) but it is not going to be installed
          Depends: libusb-1.0-0 (>= 2:1.0.8) but it is not going to be installed
          Recommends: policykit-1
 usermetricsservice : Depends: sqlite3
 wine1.6 : Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4)
           Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4)
           Recommends: winbind but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

My system is HP pavilion G6 2005AX. AMD A8,4GB RAM

Thanks,

---

### Post by dino99 on 2015-08-10
wine1.6 is outdated, try wine1.7 instead

[https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)

but you seems having installed lot of 'extra' packages, and so introduced some versions conflicts (maybe you will need to downgrade some of these to get around the conflicts)

---

