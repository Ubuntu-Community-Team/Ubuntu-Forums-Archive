---
title: "Ho to make list of dependencies"
date: 2023-06-08
forum: Installation &amp; Upgrades
---

### Post by Otto-C on 2023-06-08
On installing zoom got a list of some 26 broken packages.
How to make a list of the packages for command line or synaptic package
manager listing to install the items?
tia
otto-c

---

### Post by #&amp;thj^% on 2023-06-08
Somewhat complete:
```
apt depends zoom
zoom
  Depends: libglib2.0-0
  Depends: libxcb-keysyms1
  Depends: libxcb-xinerama0
  Depends: libdbus-1-3
  Depends: libxcb-shape0
  Depends: libxcb-shm0
  Depends: libxcb-xfixes0
  Depends: libxcb-randr0
  Depends: libxcb-image0
  Depends: libfontconfig1
  Depends: libgl1-mesa-glx
  Depends: libegl1-mesa
  Depends: libxi6
  Depends: libsm6
  Depends: libxrender1
  Depends: libpulse0
  Depends: libxcomposite1
  Depends: libxslt1.1
  Depends: libsqlite3-0
  Depends: libxcb-xtest0
  Depends: libxtst6
  Depends: ibus
    ibus:i386
  Depends: libxkbcommon-x11-0
  Depends: desktop-file-utils
    desktop-file-utils:i386
  Depends: libgbm1
  Depends: libdrm2
  Depends: libxcb-cursor0
  Depends: libfreetype6 (>= 2.6)
```
Or for a text file:
```
apt depends zoom >zoom-depnds.txt
```
Whatever location you start from, that is where the file is, as it is now it's located in my home.
EDIT for a compare:
```
apt show zoom
Package: zoom
Version: 5.14.7.2928
Priority: optional
Section: default
Maintainer: Zoom Linux Team <https://support.zoom.us>
Installed-Size: 624 MB
Depends: libglib2.0-0, libxcb-keysyms1, libxcb-xinerama0, libdbus-1-3, libxcb-shape0, libxcb-shm0, libxcb-xfixes0, libxcb-randr0, libxcb-image0, libfontconfig1, libgl1-mesa-glx, libegl1-mesa, libxi6, libsm6, libxrender1, libpulse0, libxcomposite1, libxslt1.1, libsqlite3-0, libxcb-xtest0, libxtst6, ibus, libxkbcommon-x11-0, desktop-file-utils, libgbm1, libdrm2, libxcb-cursor0, libfreetype6 (>= 2.6)
Homepage: https://www.zoom.us
License: see https://www.zoom.us/
Vendor: Zoom Video Communications, Inc.
Download-Size: 169 MB
APT-Manual-Installed: yes
APT-Sources: http://repo.linuxliteos.com/linuxlite fluorite/main amd64 Packages
Description: Zoom Cloud Meetings 
 Zoom brings people together to connect and get more done in a frictionless, secure video environment. Our easy, reliable, and innovative video-first solutions provide video meetings and chat, with additional options for webinars and phone service. 
 .
 Zoom is the leading unified communications platform and helps individuals, schools, healthcare professionals and enterprises stay connected. Visit blog.zoom.us and follow @zoom_us. 
 .
 By installing this app, you agree to our Terms of Service (https://zoom.us/terms) and Privacy Statement (https://zoom.us/privacy).


```

---

### Post by ajohnl on 2023-06-09
This might help
[https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file](https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file)

but when I have attempted to do what you are trying to do adding can cause yet more dependency problems.

Sometimes if the app has a web page dependencies may be listed on the basis of versions > xxx.......... or that can come out when compiling.

---

