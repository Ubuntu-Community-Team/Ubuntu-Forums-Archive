---
title: "Upgrade problems 17.10 to 18.04, please help!"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by fa3d on 2018-09-20
I have been trying to upgrade my Ubuntu machine from 17.10 to 18.04 for _weeks_ now but every time I try I end up needing to restore the machine from a backup. I hope someone can help me. 

This is what i have done:

1) Try to update using software updater. i get message saying "An unresolvable problem occurred while calculating the upgrade."

2) After using the command ```
grep Broken /var/log/dist-upgrade/apt.log
``` I get the following results:
```
Broken libegl1:amd64 Depends on libegl-mesa0:amd64 < none | 18.0.0~rc5-1ubuntu1 @un uH >
Broken libegl1:amd64 Depends on libegl-vendor:amd64 < none @un H >
Broken libwebkit2gtk-4.0-37:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken libyelp0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken gnome-session-bin:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken libgoa-backend-1.0-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken zenity:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgstreamer-gl1.0-0:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken gstreamer1.0-gl:amd64 Depends on libgstreamer-gl1.0-0:amd64 < none | 1.14.0-2ubuntu1 @un uH > (>= 1.14.0)
Broken gnome-online-accounts:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (= 3.28.0-0ubuntu2)
Broken gir1.2-webkit2-4.0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.19.4)
Broken gnome-startup-applications:amd64 Depends on gnome-session-bin:amd64 < 3.26.1-0ubuntu6 | 3.28.1-0ubuntu2 @ii umH > (>= 3.28.1-0ubuntu2)
Broken libcilkrts5:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libubsan0:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken ubuntu-session:amd64 Depends on gnome-session-bin:amd64 < 3.26.1-0ubuntu6 | 3.28.1-0ubuntu2 @ii umH > (>= 3.28.1-0ubuntu2)
Broken libmutter-2-0:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken rhythmbox-plugins:amd64 Depends on gir1.2-webkit2-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR >
Broken librubberband2:amd64 Conflicts on librubberband2v5:amd64 < 1.8.1-6ubuntu2 @ii mK Ib >
Broken mutter:amd64 Depends on libmutter-2-0:amd64 < none | 3.28.1-1ubuntu1 @un uH > (>= 3.27.91)
Broken libasan4:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken gir1.2-mutter-2:amd64 Depends on libmutter-2-0:amd64 < none | 3.28.1-1ubuntu1 @un uH > (= 3.28.1-1ubuntu1)
Broken libgcc-6-dev:amd64 Depends on libubsan0:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 6.4.0-17ubuntu1)
Broken libsmbios-c2:amd64 Conflicts on libsmbios2v5:amd64 < 2.3.1-0ubuntu2 @ii mK Ib >
Broken libx32ubsan0:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libx32cilkrts5:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken apturl:amd64 Depends on gir1.2-webkit2-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR >
Broken libx32asan4:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libedataserverui-1.2-2:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken marco:amd64 Depends on zenity:amd64 < 3.24.0-1 | 3.28.1-1 @ii umR >
Broken shotwell:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libx32gcc-7-dev:amd64 Depends on libx32asan4:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken kicad:amd64 Depends on libcurl4:amd64 < none | 7.58.0-2ubuntu3 @un uH > (>= 7.16.2)
Broken lib32cilkrts5:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken lib32ubsan0:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken lib32asan4:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken gir1.2-gst-plugins-base-1.0:amd64 Depends on libgstreamer-gl1.0-0:amd64 < none | 1.14.0-2ubuntu1 @un uH > (>= 1.14.0)
Broken lib32gcc-7-dev:amd64 Depends on lib32asan4:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken metacity:amd64 Depends on zenity:amd64 < 3.24.0-1 | 3.28.1-1 @ii umR >
Broken php7.2-curl:amd64 Depends on libcurl4:amd64 < none | 7.58.0-2ubuntu3 @un uH > (>= 7.44.0)
Broken gir1.2-totemplparser-1.0:amd64 Conflicts on gir1.2-totem-plparser-1.0:amd64 < 3.10.8-3ubuntu1 @ii mK >
Broken libstdc++-6-dev:amd64 Depends on libgcc-6-dev:amd64 < 6.4.0-8ubuntu1 | 6.4.0-17ubuntu1 @ii umR > (= 6.4.0-17ubuntu1)
Broken gcc-6:amd64 Depends on libgcc-6-dev:amd64 < 6.4.0-8ubuntu1 | 6.4.0-17ubuntu1 @ii umR > (= 6.4.0-17ubuntu1)
Broken php-curl:amd64 Depends on php7.2-curl:amd64 < none | 7.2.3-1ubuntu1 @un uH >
Broken cmake:amd64 Depends on libcurl4:amd64 < none | 7.58.0-2ubuntu3 @un uH > (>= 7.16.2)
Broken nautilus-share:amd64 Depends on apturl:amd64 < 0.5.2ubuntu13 | 0.5.2ubuntu14 @ii umR >
Broken gnome-calendar:amd64 Depends on libedataserverui-1.2-2:amd64 < none | 3.28.1-1ubuntu1 @un uH > (>= 3.17.1)
Broken gstreamer1.0-vaapi:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken deja-dup:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken mpv:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken cmake-qt-gui:amd64 Depends on cmake:amd64 < 3.9.1-1 | 3.10.2-1ubuntu2 @ii umR > (= 3.10.2-1ubuntu2)
Broken gnome-initial-setup:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken libssl-dev:amd64 Conflicts on libssl1.0-dev:amd64 < 1.0.2g-1ubuntu13.5 -> 1.0.2n-1ubuntu5 @ii umU Ib >
Broken g++-6:amd64 Depends on gcc-6:amd64 < 6.4.0-8ubuntu1 | 6.4.0-17ubuntu1 @ii umR > (= 6.4.0-17ubuntu1)
Broken libswt-gnome-gtk-3-jni:amd64 Depends on libswt-gtk-3-jni:amd64 < 3.8.2-4 -> 3.8.2-5 @ii umU > (= 3.8.2-4)
Broken gnome-todo:amd64 Depends on libedataserverui-1.2-2:amd64 < none | 3.28.1-1ubuntu1 @un uH > (>= 3.17.1)
Broken ubuntu-desktop:amd64 Depends on ubuntu-session:amd64 < 3.26.1-0ubuntu6 | 3.28.1-0ubuntu2 @ii umR >
Broken libopencv-imgcodecs3.1:amd64 Depends on gdal-abi-2-2-1:amd64 < none @un H >
Broken libedataserverui-1.2-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.5.3)
Broken libqt5gui5:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken yelp:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.5.3)
Broken yelp:amd64 Depends on libyelp0:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR > (= 3.26.0-1ubuntu2)
Broken gnome-shell:amd64 Depends on libmutter-2-0:amd64 < none | 3.28.1-1ubuntu1 @un uH > (>= 3.27.91)
Broken libqt5widgets5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta)
Broken libqt5svg5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.5+dfsg~)
Broken qt5-gtk-platformtheme:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (= 5.9.5+dfsg-0ubuntu1)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken libecal-1.2-19:amd64 Conflicts on gnome-calendar:amd64 < 3.26.2-1 | 3.28.1-1ubuntu2 @ii umH Ib > (< 3.26.2-3)
Broken gnome-user-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR > (>= 3)
Broken libgoa-backend-1.0-1:amd64 Depends on libgoa-1.0-common:amd64 < 3.26.1-1ubuntu1 -> 3.28.0-0ubuntu2 @ii umU > (= 3.26.1-1ubuntu1)
Broken libgcc-7-dev:amd64 Depends on libasan4:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken libgcc-7-dev:amd64 Depends on libubsan0:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken libgcc-7-dev:amd64 Depends on libcilkrts5:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken libqt5printsupport5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.6.0~beta)
Broken libqt5quick5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta)
Broken ubuntu-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken ubuntu-release-upgrader-gtk:amd64 Depends on gir1.2-webkit2-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR >
Broken gir1.2-webkit2-4.0:amd64 Depends on gir1.2-javascriptcoregtk-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 -> 2.20.1-1 @ii umU > (= 2.20.1-0ubuntu0.17.10.1)
Broken gir1.2-webkit2-4.0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.19.4)
Broken libcilkrts5:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libubsan0:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libqt5webenginecore5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta)
Broken gnome-user-guide:amd64 Depends on gnome-user-docs:amd64 < 3.26.2.1-0ubuntu0.1 | 3.28.1-0ubuntu1 @ii umR >
Broken libasan4:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken gnome-session-flashback:amd64 Depends on metacity:amd64 < 1:3.26.0-1 | 1:3.28.0-1 @ii umR > (>= 3.17.2)
Broken python3-pyqt5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta3)
Broken libqt5help5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.0.2)
Broken python3-pyqt5.qtwebchannel:amd64 Depends on python3-pyqt5:amd64 < 5.7+dfsg-6 | 5.10.1+dfsg-1ubuntu2 @ii umR > (= 5.10.1+dfsg-1ubuntu2)
Broken libqt5opengl5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta)
Broken mate-user-guide:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken gcc-7-multilib:amd64 Depends on lib32gcc-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken libqt5designer5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.7.0)
Broken libqt5quickwidgets5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.6.0~beta)
Broken libqt5webenginewidgets5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.7.0)
Broken gnome-getting-started-docs:amd64 Depends on ubuntu-docs:amd64 < 17.10.7 | 18.04.3 @ii umR >
Broken gnome-getting-started-docs:amd64 Depends on gnome-user-docs:amd64 < 3.26.2.1-0ubuntu0.1 | 3.28.1-0ubuntu1 @ii umR >
Broken gnome-getting-started-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken metacity:amd64 Depends on metacity-common:amd64 < 1:3.26.0-1 -> 1:3.28.0-1 @ii umU > (= 1:3.26.0-1)
Broken gdm3:amd64 Depends on gnome-shell:amd64 < 3.26.2-0ubuntu0.1 | 3.28.1-0ubuntu2 @ii umR > (>= 3.19.92)
Broken python3-pyqt5.qtwebengine:amd64 Depends on python3-pyqt5.qtwebchannel:amd64 < 5.7+dfsg-6 | 5.10.1+dfsg-1ubuntu2 @ii umR > (= 5.10.1+dfsg-1ubuntu2)
Broken libqt5webengine5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.3.0)
Broken libqwt-qt5-6:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.2.0)
Broken libqt5x11extras5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.5+dfsg~)
Broken libqt5webkit5:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.9.0~beta)
Broken chrome-gnome-shell:amd64 Depends on gnome-shell:amd64 < 3.26.2-0ubuntu0.1 | 3.28.1-0ubuntu2 @ii umR >
Broken caneda:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.2.0)
Broken glogg:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.8.0)
Broken anki:amd64 Depends on python3-pyqt5:amd64 < 5.7+dfsg-6 | 5.10.1+dfsg-1ubuntu2 @ii umR > (> 5.9)
Broken phantomjs:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.0.2)
Broken phantomjs:amd64 Depends on libqt5gui5-gles:amd64 < none @un H > (>= 5.0.2)
Broken phantomjs:amd64 Depends on libqt5printsupport5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.0.2)
Broken libopencv-videoio3.1:amd64 Depends on libopencv-imgcodecs3.1:amd64 < 3.1.0+dfsg1-1~exp1ubuntu3 @ii mR > (= 3.1.0+dfsg1-1~exp1ubuntu3)
Broken libopenimageio1.6:amd64 Depends on libopencv-videoio3.1:amd64 < 3.1.0+dfsg1-1~exp1ubuntu3 @ii mR >
Broken virtualbox-5.2:amd64 Depends on libqt5gui5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.4.0)
Broken virtualbox-5.2:amd64 Depends on libqt5gui5-gles:amd64 < none @un H > (>= 5.4.0)
Broken virtualbox-5.2:amd64 Depends on libqt5opengl5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.0.2)
Broken virtualbox-5.2:amd64 Depends on libqt5opengl5-gles:amd64 < none @un H > (>= 5.0.2)
Broken virtualbox-5.2:amd64 Depends on libqt5printsupport5:amd64 < 5.9.1+dfsg-10ubuntu1 | 5.9.5+dfsg-0ubuntu1 @ii umR > (>= 5.0.2)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken libgoa-backend-1.0-1:amd64 Depends on libgoa-1.0-common:amd64 < 3.26.1-1ubuntu1 -> 3.28.0-0ubuntu2 @ii umU > (= 3.26.1-1ubuntu1)
Broken libgoa-backend-1.0-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgcc-7-dev:amd64 Depends on libasan4:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken libgcc-7-dev:amd64 Depends on libubsan0:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken libgcc-7-dev:amd64 Depends on libcilkrts5:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken ubuntu-release-upgrader-gtk:amd64 Depends on gir1.2-webkit2-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR >
Broken gir1.2-webkit2-4.0:amd64 Depends on gir1.2-javascriptcoregtk-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 -> 2.20.1-1 @ii umU > (= 2.20.1-0ubuntu0.17.10.1)
Broken gir1.2-webkit2-4.0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.19.4)
Broken gcc-multilib:amd64 Depends on gcc-7-multilib:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (>= 7.3.0-12~)
Broken libcilkrts5:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libubsan0:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken libasan4:amd64 Depends on gcc-8-base:amd64 < 8-20170923-1ubuntu2 -> 8-20180414-1ubuntu2 @ii umU > (= 8-20170923-1ubuntu2)
Broken gnome-session-flashback:amd64 Depends on metacity:amd64 < 1:3.26.0-1 | 1:3.28.0-1 @ii umR > (>= 3.17.2)
Broken metacity:amd64 Depends on metacity-common:amd64 < 1:3.26.0-1 -> 1:3.28.0-1 @ii umU > (= 1:3.26.0-1)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken libgcc-7-dev:amd64 Depends on libasan4:amd64 < 8-20170923-1ubuntu2 @ii mR > (>= 7.3.0-16ubuntu3)
Broken ubuntu-release-upgrader-gtk:amd64 Depends on gir1.2-webkit2-4.0:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR >
Broken update-manager:amd64 Depends on ubuntu-release-upgrader-gtk:amd64 < 1:17.10.11 | 1:18.04.17 @ii umR >
Broken update-notifier:amd64 Depends on update-manager-gnome:amd64 < none @un H >
Broken update-notifier:amd64 Depends on update-manager:amd64 < 1:17.10.13 | 1:18.04.11 @ii umR > (>= 1:17.04.3)
Broken update-notifier:amd64 Depends on ubuntu-release-upgrader-gtk:amd64 < 1:17.10.11 | 1:18.04.17 @ii umR >
Broken gnome-session-flashback:amd64 Depends on metacity:amd64 < 1:3.26.0-1 | 1:3.28.0-1 @ii umR > (>= 3.17.2)
Broken libstdc++-7-dev:amd64 Depends on libgcc-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken libgfortran-7-dev:amd64 Depends on libgcc-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken g++-7:amd64 Depends on libstdc++-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken libobjc-7-dev:amd64 Depends on libgcc-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken gfortran-7:amd64 Depends on libgfortran-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken indicator-bluetooth:amd64 Depends on unity-control-center:amd64 < none | 15.04.0+18.04.20180216-0ubuntu1 @rc uH >
Broken gfortran:amd64 Depends on gfortran-7:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (>= 7.3.0-12~)
Broken clang-3.8:amd64 Depends on libstdc++-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR >
Broken libegl1:amd64 Depends on libegl-mesa0:amd64 < none | 18.0.0~rc5-1ubuntu1 @un uH >
Broken libegl1:amd64 Depends on libegl-vendor:amd64 < none @un H >
Broken libwebkit2gtk-4.0-37:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken libyelp0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken gcc-7:amd64 Depends on libgcc-7-dev:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (= 7.3.0-16ubuntu3)
Broken libgoa-backend-1.0-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgstreamer-gl1.0-0:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken gstreamer1.0-gl:amd64 Depends on libgstreamer-gl1.0-0:amd64 < none | 1.14.0-2ubuntu1 @un uH > (>= 1.14.0)
Broken gnome-online-accounts:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (= 3.28.0-0ubuntu2)
Broken g++:amd64 Depends on g++-7:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (>= 7.3.0-12~)
Broken unity-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.18.0)
Broken yelp:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.5.3)
Broken gcc:amd64 Depends on gcc-7:amd64 < 7.2.0-8ubuntu3.2 | 7.3.0-16ubuntu3 @ii umR > (>= 7.3.0-12~)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken gnome-user-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR > (>= 3)
Broken build-essential:amd64 Depends on gcc:amd64 < 4:7.2.0-1ubuntu1 | 4:7.3.0-3ubuntu2 @ii umR > (>= 4:7.2)
Broken ubuntu-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken dkms:amd64 Depends on gcc:amd64 < 4:7.2.0-1ubuntu1 | 4:7.3.0-3ubuntu2 @ii umR >
Broken indicator-bluetooth:amd64 Depends on unity-control-center:amd64 < none | 15.04.0+18.04.20180216-0ubuntu1 @rc uH >
Broken nvidia-390:amd64 Depends on dkms:amd64 < 2.3-3ubuntu3 | 2.3-3ubuntu9 @ii umR >
Broken libcuda1-390:amd64 Depends on nvidia-390:amd64 < 390.48-0ubuntu0~gpu17.10.3 @ii mR > (>= 390.48)
Broken bbswitch-dkms:amd64 Depends on dkms:amd64 < 2.3-3ubuntu3 | 2.3-3ubuntu9 @ii umR > (>= 2.1.0.0)
Broken nvidia-opencl-icd-390:amd64 Depends on nvidia-390:amd64 < 390.48-0ubuntu0~gpu17.10.3 @ii mR > (>= 390.48)
Broken libegl1:amd64 Depends on libegl-mesa0:amd64 < none | 18.0.0~rc5-1ubuntu1 @un uH >
Broken libegl1:amd64 Depends on libegl-vendor:amd64 < none @un H >
Broken libwebkit2gtk-4.0-37:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken libyelp0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgoa-backend-1.0-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgstreamer-gl1.0-0:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken gstreamer1.0-gl:amd64 Depends on libgstreamer-gl1.0-0:amd64 < none | 1.14.0-2ubuntu1 @un uH > (>= 1.14.0)
Broken gnome-online-accounts:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (= 3.28.0-0ubuntu2)
Broken unity-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.18.0)
Broken yelp:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.5.3)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken gnome-user-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR > (>= 3)
Broken ubuntu-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken indicator-bluetooth:amd64 Depends on unity-control-center:amd64 < none | 15.04.0+18.04.20180216-0ubuntu1 @rc uH >
Broken libegl1:amd64 Depends on libegl-mesa0:amd64 < none | 18.0.0~rc5-1ubuntu1 @un uH >
Broken libegl1:amd64 Depends on libegl-vendor:amd64 < none @un H >
Broken libwebkit2gtk-4.0-37:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken libyelp0:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgoa-backend-1.0-1:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.15.1)
Broken libgstreamer-gl1.0-0:amd64 Depends on libegl1:amd64 < none | 1.0.0-2ubuntu2 @un uH >
Broken gstreamer1.0-gl:amd64 Depends on libgstreamer-gl1.0-0:amd64 < none | 1.14.0-2ubuntu1 @un uH > (>= 1.14.0)
Broken gnome-online-accounts:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (= 3.28.0-0ubuntu2)
Broken unity-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.18.0)
Broken yelp:amd64 Depends on libwebkit2gtk-4.0-37:amd64 < 2.20.1-0ubuntu0.17.10.1 | 2.20.1-1 @ii umR > (>= 2.5.3)
Broken gnome-control-center:amd64 Depends on libgoa-backend-1.0-1:amd64 < 3.26.1-1ubuntu1 | 3.28.0-0ubuntu2 @ii umR > (>= 3.10.0)
Broken gnome-user-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR > (>= 3)
Broken ubuntu-docs:amd64 Depends on yelp:amd64 < 3.26.0-1ubuntu1 | 3.26.0-1ubuntu2 @ii umR >
Broken indicator-bluetooth:amd64 Depends on unity-control-center:amd64 < none | 15.04.0+18.04.20180216-0ubuntu1 @rc uH > 
```

3) Then I tried removing some packages from the broken package list. I tried different combinations until the updater did not gave any complaints.
After trying different combinations, I ended up removing "indicator-bluetooth" using this command:
 ```
sudo dpkg --remove --force-remove-reinstreq indicator-bluetooth   
```

4) After removing that package, I used ```
sudo do-release-upgrade
```, and this time I did not get an error and the upgrade started
 The installer tells me that some packages are going to be removed:
  ```
No longer supported: caribou ecryptfs-utils fonts-nanum fonts-symbola 
  fonts-takao-pgothic gir1.2-caribou-1.0 gir1.2-gnomekeyring-1.0 
  gnome-screensaver gnome-user-share gucharmap kerneloops-applet 
  libboost-date-time1.62.0 libboost-filesystem1.62.0 
  libboost-iostreams1.62.0 libboost-system1.62.0 
  libboost-thread1.62.0 libcanberra-gtk-module libcaribou-common 
  libcaribou0 libecryptfs1 libfreerdp-cache1.1 libfreerdp-client1.1 
  libfreerdp-codec1.1 libfreerdp-common1.1.0 libfreerdp-core1.1 
  libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1 
  libfreerdp-plugins-standard libfreerdp-primitives1.1 
  libfreerdp-utils1.1 libgnome-keyring-common libgnome-keyring0 
  libgtk2-perl libgucharmap-2-90-7 libical2 libisl15 libllvm5.0 
  libpango-perl libreoffice-style-elementary libtelepathy-glib0 
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 
  libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1 
  libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1 
  libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 
  libwinpr-rpc0.1 libwinpr-sspi0.1 libwinpr-synch0.1 
  libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1 tcl tcpd 
  tk ttf-ancient-fonts-symbola ubuntu-wallpapers-artful 

Remove: anki apturl build-essential caneda chrome-gnome-shell cmake 
  cmake-qt-gui deja-dup evolution-data-server g++ g++-6 gcc-6 gdm3 
  gfortran gir1.2-totem-plparser-1.0 glogg gnome-calendar 
  gnome-control-center gnome-getting-started-docs 
  gnome-online-accounts gnome-settings-daemon gnome-shell 
  gnome-user-docs gnome-user-guide kolourpaint libedataserverui-1.2-1 
  libgles2-mesa libgoa-backend-1.0-1 libsmbios2v5 mutter 
  nautilus-share nvidia-390 nvidia-cuda-toolkit rhythmbox-plugins 
  shotwell ubuntu-docs ubuntu-session virtualbox-5.2 

Remove (was auto installed) bbswitch-dkms clang-3.8 dkms g++-7 gcc 
  gcc-7 gcc-7-multilib gcc-multilib gfortran-7 
  gnome-session-flashback gnome-tweak-tool gstreamer1.0-vaapi kinit 
  kio kwayland-integration lib32asan4 lib32cilkrts5 lib32gcc-7-dev 
  lib32ubsan0 libasan4 libcilkrts5 libcuda1-390 libcuinj64-8.0 
  libdbusmenu-qt5 libgcc-6-dev libgcc-7-dev libgfortran-7-dev 
  libkf5auth5 libkf5bookmarks5 libkf5completion5 libkf5configgui5 
  libkf5configwidgets5 libkf5crash5 libkf5dbusaddons5 
  libkf5globalaccel-bin libkf5globalaccel5 libkf5globalaccelprivate5 
  libkf5guiaddons5 libkf5iconthemes-bin libkf5iconthemes5 
  libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 
  libkf5kdelibs4support5 libkf5kdelibs4support5-bin libkf5kiocore5 
  libkf5kiofilewidgets5 libkf5kiowidgets5 libkf5notifications5 
  libkf5parts-plugins libkf5parts5 libkf5sane5 libkf5service-bin 
  libkf5service5 libkf5solid5 libkf5sonnetui5 libkf5textwidgets5 
  libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 
  libkf5widgetsaddons5 libkf5windowsystem5 libkf5xmlgui5 
  libkwalletbackend5-5 libobjc-7-dev libopencv-imgcodecs3.1 
  libopencv-videoio3.1 libopenimageio1.6 libphonon4qt5-4 
  libpolkit-qt5-1-1 libqt5designer5 libqt5gui5 libqt5help5 
  libqt5opengl5 libqt5printsupport5 libqt5quick5 libqt5quickwidgets5 
  libqt5svg5 libqt5waylandclient5 libqt5waylandcompositor5 
  libqt5webenginecore5 libqt5webenginewidgets5 libqt5widgets5 
  libqt5x11extras5 libqwt-qt5-6 librubberband2v5 libssl1.0-dev 
  libstdc++-6-dev libstdc++-7-dev libswt-gnome-gtk-3-jni libubsan0 
  libx32asan4 libx32cilkrts5 libx32gcc-7-dev libx32ubsan0 marco 
  mate-user-guide metacity mpv nvidia-cuda-dev nvidia-opencl-icd-390 
  nvidia-profiler nvidia-visual-profiler phonon4qt5 
  phonon4qt5-backend-vlc python3-pyqt5 python3-pyqt5.qtwebchannel 
  python3-pyqt5.qtwebengine qt5-gtk-platformtheme qtwayland5 
```


5) The installation ends with Errors:
 ```
Errors were encountered while processing:
 ubuntu-desktop
Exception during pm.DoInstall():  E:Sub-process /usr/bin/dpkg returned an error code (1)

Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gdm3; however:
  Package gdm3 is not installed.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not installed.
 ubuntu-desktop depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not installed.
 ubuntu-desktop depends on gnome-shell; however:
  Package gnome-shell is not installed.
 ubuntu-desktop depends on ubuntu-session; however:
  Package ubuntu-session is not installed.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop
```

6) After this point I try sifferent commands like ```
sudo apt --fix-broken install
```, and I really dont know what to do. 
When I restart the machine I have no GUI and only starts from the command line. I open the application TimeShift from the terminal and restore a backup to recover my previous OS configuration. 

Any ideas?

---

### Post by linux4me on 2018-09-20
I always do a clean install, and never try to use the update method.

---

### Post by fa3d on 2018-09-20
> **linux4me said:**
> I always do a clean install, and never try to use the update method.
That is what I have been trying to avoid as I have spent a lot of time installing and configuring stuff in my current ubuntu version and I don't want to loose it. 

If I don't find a solution probably I'll keep my current ubuntu version for some time and one day in the future I will make a clean install and try to install everything again

---

### Post by linux4me on 2018-09-20
The majority of your configuration settings should be in your /home folder, though many will be in hidden folders, so if you back that up and include the hidden folders, then copy it over to the fresh install, you should have most of them. Installing your apps from Terminal in one command speeds up that process. I don't know how much tweaking you've done, but I would think a clean install and re-installing all your apps should take far less time than you've already spent. Since the [end-of-life for 17.10]("https://wiki.ubuntu.com/Releases") was 6/19/2018, I don't recommend sticking with it.

---

### Post by fa3d on 2018-09-22
OK, I finally decided to do a clean installation. I used "Aptik" to save  list of installed files, sources, etc., and usd DejaDup (Ubuntu default  backup) to save my home folder to a NAS drive. 

After the install of the latest Ubuntu version, I am trying to restore but I get an error:
```

Invalid data - SHA1 hash mismatch for file:
 duplicity-full.20180919T135536Z.vol1825.difftar.gpg
 Calculated hash: 56f1400a018c190679e7f751202bd62dc7667cf2
 Manifest hash: 20290ca0bd406f206453df2f4f77fbe5d10a8dd1

```

Some files were restored but the restore process stops at that point. I have been searching for a solution but havent found one. I think now I have to open another thread :(

---

