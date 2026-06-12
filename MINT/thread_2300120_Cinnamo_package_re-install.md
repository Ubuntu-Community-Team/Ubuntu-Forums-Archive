---
title: "Cinnamo package re-install"
date: 2015-10-23
forum: MINT
---

### Post by deepakdeshp on 2015-10-23
Hello,

I am using Mint 17.2 Which is based on Ubuntu 14.04. My Cinnamon desktop broke and gives error Cinnamon crashed Going to fallback mode. This is a general question

Can I reinstall the cinnamon packages without loosing their configuration? The command below gives list of installed Cinnamon packages .. can it be extended to reinstall these packages without losing configuration?

```
aptitude search cinnamon | grep ^ii   cinnamon                        - Modern Linux desktop                      
i   cinnamon-bluetooth              - Gnome Bluetooth support for the Cinnamon d
i   cinnamon-common                 - Cinnamon desktop (Common data files)      
i   cinnamon-control-center         - utilities to configure the Cinnamon deskto
i   cinnamon-control-center-data    - configuration applets for Cinnamon - data 
i   cinnamon-desktop-data           - Common files for Cinnamon desktop apps    
i   cinnamon-screensaver            - Cinnamon screen saver and locker          
i   cinnamon-session                - Cinnamon Session Manager - Minimal runtime
i   cinnamon-session-common         - Cinnamon Session Manager - common files   
i   cinnamon-settings-daemon        - daemon handling the Cinnamon session setti
i   cinnamon-themes                 - Cinnamon themes                           
i   cinnamon-translations           - Translation files for the Cinnamon desktop
i   gir1.2-cinnamondesktop-3.0      - Introspection data for CinnamonDesktop    
i   libcinnamon-control-center1     - utilities to configure the Cinnamon deskto
i   libcinnamon-desktop4            - Cinnamon library for loading .desktop file
i   libcinnamon-menu-3-0            - Cinnamon implementation of the freedesktop
i   mint-artwork-cinnamon           - Default artwork for the Cinnamon edition o
i   mint-info-cinnamon              - Necessary information about the Linux Mint
i   mint-user-guide-cinnamon        - The Linux Mint User Guide - Cinnamon Editi


$aptitude search cinnamon | grep ^i|awk -F ' ' '{print $2}'
cinnamon
cinnamon-bluetooth
cinnamon-common
cinnamon-control-center
cinnamon-control-center-data
cinnamon-desktop-data
cinnamon-screensaver
cinnamon-session
cinnamon-session-common
cinnamon-settings-daemon
cinnamon-themes
cinnamon-translations
gir1.2-cinnamondesktop-3.0
libcinnamon-control-center1
libcinnamon-desktop4
libcinnamon-menu-3-0
mint-artwork-cinnamon
mint-info-cinnamon
mint-user-guide-cinnamon


```

---

### Post by howefield on 2015-10-23
Thread moved to the "*MINT*" forum.

---

### Post by deepakdeshp on 2015-10-23
I installed the packages but I guess they arent installed properly. I have posted /var/log/dpkg.log file


**The status is half configured packages **as shown in the dpkg.log code below


```

**#!/bin/bash**
**for i in `aptitude search cinnamon | grep ^i|awk -F ' ' '{print $2}'`**
**    do**
**         sudo apt-get install --reinstall $i**
**    done**

2015-10-24 01:06:09 status half-configured libc-bin:amd64 2.19-22
2015-10-24 01:06:09 status installed libc-bin:amd64 2.19-22
2015-10-24 02:20:40 startup archives unpack
2015-10-24 02:20:41 upgrade cinnamon:amd64 2.8.0-20151023040014-trusty 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status half-configured cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status unpacked cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status half-installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:20:41 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:20:41 status half-installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:20:41 status half-installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:41 status triggers-pending mime-support:all 3.59
2015-10-24 02:20:41 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:20:41 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:20:41 status half-installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:42 status half-installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:42 status unpacked cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:42 status unpacked cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:42 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-10-24 02:20:42 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:20:42 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:20:43 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:20:43 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:20:43 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:20:43 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:20:43 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:20:43 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:20:43 trigproc mime-support:all 3.59 <none>
2015-10-24 02:20:43 status half-configured mime-support:all 3.59
2015-10-24 02:20:44 status installed mime-support:all 3.59
2015-10-24 02:20:44 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:20:44 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:20:44 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:20:44 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:20:44 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:20:44 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:20:45 startup packages configure
2015-10-24 02:20:45 configure cinnamon:amd64 2.8.0-20151023040014-trusty <none>
2015-10-24 02:20:45 status unpacked cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:45 status half-configured cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:45 status installed cinnamon:amd64 2.8.0-20151023040014-trusty
2015-10-24 02:20:45 status triggers-pending libc-bin:amd64 2.19-22
2015-10-24 02:20:45 trigproc libc-bin:amd64 2.19-22 <none>
2015-10-24 02:20:45 status half-configured libc-bin:amd64 2.19-22
2015-10-24 02:20:45 status installed libc-bin:amd64 2.19-22
2015-10-24 02:21:09 startup archives unpack
2015-10-24 02:21:09 upgrade cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty 3.8.11-20151023012003-trusty
2015-10-24 02:21:09 status half-configured cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:09 status unpacked cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:09 status half-installed cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:09 status triggers-pending mime-support:all 3.59
2015-10-24 02:21:09 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:21:09 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:21:09 status half-installed cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:09 status half-installed cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:10 status unpacked cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:10 status unpacked cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:10 trigproc mime-support:all 3.59 <none>
2015-10-24 02:21:10 status half-configured mime-support:all 3.59
2015-10-24 02:21:11 status installed mime-support:all 3.59
2015-10-24 02:21:11 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:21:11 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:21:11 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:21:11 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:21:11 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:21:11 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:21:11 startup packages configure
2015-10-24 02:21:11 configure cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty <none>
2015-10-24 02:21:11 status unpacked cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:11 status half-configured cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:11 status installed cinnamon-bluetooth:amd64 3.8.11-20151023012003-trusty
2015-10-24 02:21:45 startup archives unpack
2015-10-24 02:21:46 upgrade cinnamon-common:all 2.8.0-20151023040014-trusty 2.8.0-20151023040014-trusty
2015-10-24 02:21:46 status half-configured cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:46 status unpacked cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:46 status half-installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:47 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-10-24 02:21:47 status half-installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:47 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:21:48 status half-installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:48 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:21:48 status half-installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:48 status half-installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:48 status unpacked cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:48 status unpacked cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:48 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-10-24 02:21:48 status half-configured hicolor-icon-theme:all 0.13-1
2015-10-24 02:21:56 status installed hicolor-icon-theme:all 0.13-1
2015-10-24 02:21:56 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:21:56 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:21:57 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:21:57 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:21:57 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:21:57 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:21:57 startup packages configure
2015-10-24 02:21:57 configure cinnamon-common:all 2.8.0-20151023040014-trusty <none>
2015-10-24 02:21:57 status unpacked cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:57 status unpacked cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:57 status half-configured cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:21:57 status installed cinnamon-common:all 2.8.0-20151023040014-trusty
2015-10-24 02:22:05 startup archives unpack
2015-10-24 02:22:06 upgrade cinnamon-control-center:amd64 2.8.1-20151023013043-trusty 2.8.1-20151023013043-trusty
2015-10-24 02:22:06 status half-configured cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:06 status unpacked cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:06 status half-installed cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:07 status triggers-pending menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:07 status half-installed cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:07 status triggers-pending mime-support:all 3.59
2015-10-24 02:22:07 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:22:07 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:22:07 status half-installed cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:07 status half-installed cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:07 status triggers-awaited menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:07 status unpacked cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:07 status unpacked cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:08 trigproc menu:amd64 2.1.46ubuntu1 <none>
2015-10-24 02:22:08 status half-configured menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:09 status installed menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:09 trigproc mime-support:all 3.59 <none>
2015-10-24 02:22:09 status half-configured mime-support:all 3.59
2015-10-24 02:22:10 status installed mime-support:all 3.59
2015-10-24 02:22:10 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:22:10 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:22:10 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:22:10 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:22:10 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:22:10 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:22:10 startup packages configure
2015-10-24 02:22:10 configure cinnamon-control-center:amd64 2.8.1-20151023013043-trusty <none>
2015-10-24 02:22:10 status unpacked cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:10 status unpacked cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:10 status half-configured cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:11 status installed cinnamon-control-center:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:22:11 status triggers-pending menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:11 status triggers-awaited menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:11 trigproc menu:amd64 2.1.46ubuntu1 <none>
2015-10-24 02:22:11 status half-configured menu:amd64 2.1.46ubuntu1
2015-10-24 02:22:11 status installed menu:amd64 2.1.46ubuntu1
2015-10-24 02:23:00 startup archives unpack
2015-10-24 02:23:01 upgrade cinnamon-control-center-data:all 2.8.1-20151023013043-trusty 2.8.1-20151023013043-trusty
2015-10-24 02:23:01 status half-configured cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:01 status unpacked cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:01 status half-installed cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:01 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:02 status half-installed cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:02 status half-installed cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:02 status unpacked cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:02 status unpacked cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:03 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-10-24 02:23:03 status half-configured hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:04 status installed hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:05 startup packages configure
2015-10-24 02:23:05 configure cinnamon-control-center-data:all 2.8.1-20151023013043-trusty <none>
2015-10-24 02:23:05 status unpacked cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:05 status unpacked cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:05 status half-configured cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:05 status installed cinnamon-control-center-data:all 2.8.1-20151023013043-trusty
2015-10-24 02:23:10 startup archives unpack
2015-10-24 02:23:11 upgrade cinnamon-desktop-data:all 2.8.0-20151023000442-trusty 2.8.0-20151023000442-trusty
2015-10-24 02:23:11 status half-configured cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:11 status unpacked cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:11 status half-installed cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:11 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:11 status half-installed cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:11 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:11 status half-installed cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:12 status half-installed cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:12 status unpacked cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:12 status unpacked cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:12 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:23:12 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:12 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:12 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:23:12 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:13 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:13 startup packages configure
2015-10-24 02:23:13 configure cinnamon-desktop-data:all 2.8.0-20151023000442-trusty <none>
2015-10-24 02:23:13 status unpacked cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:13 status half-configured cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:13 status installed cinnamon-desktop-data:all 2.8.0-20151023000442-trusty
2015-10-24 02:23:18 startup archives unpack
2015-10-24 02:23:19 upgrade cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty 2.8.0-20151023013228-trusty
2015-10-24 02:23:19 status half-configured cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:19 status unpacked cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:19 status half-installed cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:19 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:19 status triggers-pending mime-support:all 3.59
2015-10-24 02:23:19 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:23:19 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:23:19 status half-installed cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:20 status half-installed cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:20 status unpacked cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:20 status unpacked cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:20 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-10-24 02:23:20 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:21 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:21 trigproc mime-support:all 3.59 <none>
2015-10-24 02:23:21 status half-configured mime-support:all 3.59
2015-10-24 02:23:21 status installed mime-support:all 3.59
2015-10-24 02:23:21 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:23:21 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:23:22 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:23:22 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:23:22 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:23:22 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:23:22 startup packages configure
2015-10-24 02:23:22 configure cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty <none>
2015-10-24 02:23:22 status unpacked cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:22 status unpacked cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:22 status half-configured cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:22 status installed cinnamon-screensaver:amd64 2.8.0-20151023013228-trusty
2015-10-24 02:23:28 startup archives unpack
2015-10-24 02:23:28 upgrade cinnamon-session:amd64 2.8.0-20151023043024-trusty 2.8.0-20151023043024-trusty
2015-10-24 02:23:28 status half-configured cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:28 status unpacked cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:28 status half-installed cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:28 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:28 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:29 status half-installed cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:29 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:29 status half-installed cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:29 status half-installed cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:29 status unpacked cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:29 status unpacked cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:29 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-10-24 02:23:29 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:30 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:30 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:23:30 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:30 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:30 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:23:30 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:30 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:31 startup packages configure
2015-10-24 02:23:31 configure cinnamon-session:amd64 2.8.0-20151023043024-trusty <none>
2015-10-24 02:23:31 status unpacked cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:31 status half-configured cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:31 status installed cinnamon-session:amd64 2.8.0-20151023043024-trusty
2015-10-24 02:23:37 startup archives unpack
2015-10-24 02:23:38 upgrade cinnamon-session-common:all 2.8.0-20151023043024-trusty 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status half-configured cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status unpacked cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status half-installed cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:38 status half-installed cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status half-installed cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status unpacked cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:38 status unpacked cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:39 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-10-24 02:23:39 status half-configured hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:40 status installed hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:41 startup packages configure
2015-10-24 02:23:41 configure cinnamon-session-common:all 2.8.0-20151023043024-trusty <none>
2015-10-24 02:23:41 status unpacked cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:41 status unpacked cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:41 status half-configured cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:41 status installed cinnamon-session-common:all 2.8.0-20151023043024-trusty
2015-10-24 02:23:56 startup archives unpack
2015-10-24 02:23:57 upgrade cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty 2.8.0-20151023004503-trusty
2015-10-24 02:23:57 status half-configured cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:57 status unpacked cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:57 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:57 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-10-24 02:23:57 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:57 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:23:57 status triggers-pending mime-support:all 3.59
2015-10-24 02:23:57 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:23:57 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:23:58 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:58 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:23:58 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:58 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:23:58 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:59 status half-installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:59 status unpacked cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:59 status unpacked cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:23:59 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-10-24 02:23:59 status half-configured hicolor-icon-theme:all 0.13-1
2015-10-24 02:24:01 status installed hicolor-icon-theme:all 0.13-1
2015-10-24 02:24:01 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-10-24 02:24:01 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:24:02 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-10-24 02:24:02 trigproc mime-support:all 3.59 <none>
2015-10-24 02:24:02 status half-configured mime-support:all 3.59
2015-10-24 02:24:03 status installed mime-support:all 3.59
2015-10-24 02:24:03 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:24:03 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:24:03 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:24:03 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:24:03 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:24:03 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:24:03 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:24:03 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:24:03 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:24:03 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:24:03 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:24:03 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:24:04 startup packages configure
2015-10-24 02:24:04 configure cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty <none>
2015-10-24 02:24:04 status unpacked cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:24:04 status unpacked cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:24:04 status half-configured cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:24:04 status installed cinnamon-settings-daemon:amd64 2.8.0-20151023004503-trusty
2015-10-24 02:24:14 startup archives unpack
2015-10-24 02:24:14 upgrade cinnamon-themes:all 2015.06.14 2015.06.14
2015-10-24 02:24:14 status half-configured cinnamon-themes:all 2015.06.14
2015-10-24 02:24:15 status unpacked cinnamon-themes:all 2015.06.14
2015-10-24 02:24:15 status half-installed cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 status half-installed cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 status unpacked cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 status unpacked cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 startup packages configure
2015-10-24 02:24:16 configure cinnamon-themes:all 2015.06.14 <none>
2015-10-24 02:24:16 status unpacked cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 status half-configured cinnamon-themes:all 2015.06.14
2015-10-24 02:24:16 status installed cinnamon-themes:all 2015.06.14
2015-10-24 02:24:53 startup archives unpack
2015-10-24 02:24:53 upgrade cinnamon-translations:all 2.8.0-20151023040309-trusty 2.8.0-20151023040309-trusty
2015-10-24 02:24:53 status half-configured cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:53 status unpacked cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:53 status half-installed cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:55 status half-installed cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:55 status unpacked cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:56 status unpacked cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:56 startup packages configure
2015-10-24 02:24:56 configure cinnamon-translations:all 2.8.0-20151023040309-trusty <none>
2015-10-24 02:24:56 status unpacked cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:56 status half-configured cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:24:56 status installed cinnamon-translations:all 2.8.0-20151023040309-trusty
2015-10-24 02:25:01 startup archives unpack
2015-10-24 02:25:01 upgrade gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status half-configured gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status unpacked gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status half-installed gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status half-installed gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status unpacked gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:01 status unpacked gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:02 startup packages configure
2015-10-24 02:25:02 configure gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty <none>
2015-10-24 02:25:02 status unpacked gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:02 status half-configured gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:02 status installed gir1.2-cinnamondesktop-3.0:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:06 startup archives unpack
2015-10-24 02:25:07 upgrade libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status half-configured libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status unpacked libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status half-installed libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status half-installed libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status unpacked libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:07 status unpacked libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:08 startup packages configure
2015-10-24 02:25:08 configure libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty <none>
2015-10-24 02:25:08 status unpacked libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:08 status half-configured libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:08 status installed libcinnamon-control-center1:amd64 2.8.1-20151023013043-trusty
2015-10-24 02:25:08 status triggers-pending libc-bin:amd64 2.19-22
2015-10-24 02:25:08 trigproc libc-bin:amd64 2.19-22 <none>
2015-10-24 02:25:08 status half-configured libc-bin:amd64 2.19-22
2015-10-24 02:25:08 status installed libc-bin:amd64 2.19-22
2015-10-24 02:25:14 startup archives unpack
2015-10-24 02:25:15 upgrade libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status half-configured libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status unpacked libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status half-installed libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status half-installed libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status unpacked libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status unpacked libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 startup packages configure
2015-10-24 02:25:15 configure libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty <none>
2015-10-24 02:25:15 status unpacked libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:15 status half-configured libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:16 status installed libcinnamon-desktop4:amd64 2.8.0-20151023000442-trusty
2015-10-24 02:25:16 status triggers-pending libc-bin:amd64 2.19-22
2015-10-24 02:25:16 trigproc libc-bin:amd64 2.19-22 <none>
2015-10-24 02:25:16 status half-configured libc-bin:amd64 2.19-22
2015-10-24 02:25:16 status installed libc-bin:amd64 2.19-22
2015-10-24 02:25:21 startup archives unpack
2015-10-24 02:25:22 upgrade libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty 2.8.0-20151023012125-trusty
2015-10-24 02:25:22 status half-configured libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:22 status unpacked libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:22 status half-installed libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status half-installed libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status unpacked libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status unpacked libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 startup packages configure
2015-10-24 02:25:23 configure libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty <none>
2015-10-24 02:25:23 status unpacked libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status half-configured libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status installed libcinnamon-menu-3-0:amd64 2.8.0-20151023012125-trusty
2015-10-24 02:25:23 status triggers-pending libc-bin:amd64 2.19-22
2015-10-24 02:25:23 trigproc libc-bin:amd64 2.19-22 <none>
2015-10-24 02:25:23 status half-configured libc-bin:amd64 2.19-22
2015-10-24 02:25:24 status installed libc-bin:amd64 2.19-22
2015-10-24 02:25:30 startup archives unpack
2015-10-24 02:25:30 upgrade mint-artwork-cinnamon:all 4.9 4.9
2015-10-24 02:25:30 status half-configured mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:30 status unpacked mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:30 status half-installed mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:30 status triggers-pending libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:25:30 status half-installed mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:30 status triggers-pending libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:25:30 status half-installed mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:31 status half-installed mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:31 status unpacked mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:31 status unpacked mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:31 trigproc libglib2.0-0:i386 2.40.2-0ubuntu1 <none>
2015-10-24 02:25:31 status half-configured libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:25:31 status installed libglib2.0-0:i386 2.40.2-0ubuntu1
2015-10-24 02:25:31 trigproc libglib2.0-0:amd64 2.40.2-0ubuntu1 <none>
2015-10-24 02:25:31 status half-configured libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:25:31 status installed libglib2.0-0:amd64 2.40.2-0ubuntu1
2015-10-24 02:25:32 startup packages configure
2015-10-24 02:25:32 configure mint-artwork-cinnamon:all 4.9 <none>
2015-10-24 02:25:32 status unpacked mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:32 status unpacked mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:32 status half-configured mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:34 status installed mint-artwork-cinnamon:all 4.9
2015-10-24 02:25:38 startup archives unpack
2015-10-24 02:25:39 upgrade mint-info-cinnamon:amd64 2015.06.08 2015.06.08
2015-10-24 02:25:39 status half-configured mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:39 status unpacked mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:39 status half-installed mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:39 status half-installed mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:39 status unpacked mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:39 status unpacked mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:40 startup packages configure
2015-10-24 02:25:40 configure mint-info-cinnamon:amd64 2015.06.08 <none>
2015-10-24 02:25:40 status unpacked mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:40 status unpacked mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:40 status half-configured mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:25:40 status installed mint-info-cinnamon:amd64 2015.06.08
2015-10-24 02:26:13 startup archives unpack
2015-10-24 02:26:14 upgrade mint-user-guide-cinnamon:all 17.1.0 17.1.0
2015-10-24 02:26:14 status half-configured mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:14 status unpacked mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:14 status half-installed mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:14 status triggers-pending mime-support:all 3.59
2015-10-24 02:26:14 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:26:14 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:26:14 status half-installed mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:15 status half-installed mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:15 status unpacked mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:15 status unpacked mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:15 trigproc mime-support:all 3.59 <none>
2015-10-24 02:26:15 status half-configured mime-support:all 3.59
2015-10-24 02:26:16 status installed mime-support:all 3.59
2015-10-24 02:26:16 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-10-24 02:26:16 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:26:16 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-10-24 02:26:16 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-10-24 02:26:16 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:26:16 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-10-24 02:26:16 startup packages configure
2015-10-24 02:26:16 configure mint-user-guide-cinnamon:all 17.1.0 <none>
2015-10-24 02:26:16 status unpacked mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:16 status half-configured mint-user-guide-cinnamon:all 17.1.0
2015-10-24 02:26:17 status installed mint-user-guide-cinnamon:all 17.1.0
uma@uma-HP-Notebook:/tmp$ 



```

---

### Post by Habitual on 2015-10-23
Fallback mode refers to video does it not?
half-installed doesn't look right either.
[http://askubuntu.com/questions/490671/fix-half-installed-package](http://askubuntu.com/questions/490671/fix-half-installed-package)

---

### Post by deepakdeshp on 2015-10-24
Thank you. I googled to find how to locate half installed software but I didnt get any clue. There is a bug in Mint apt too  . The thread below explains it. I had opened a thread in Mint forums which has given this information. The Mint forum people are helping me with this.

[http://forums.linuxmint.com/viewtopic.php?f=47&t=207897&p=1083995&sid=187a7384955173db86797c7675d6f916#p1083995](http://forums.linuxmint.com/viewtopic.php?f=47&t=207897&p=1083995&sid=187a7384955173db86797c7675d6f916#p1083995)

---

