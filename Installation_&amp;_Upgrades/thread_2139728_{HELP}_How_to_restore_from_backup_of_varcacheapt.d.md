---
title: "{HELP} How to restore from backup of /var/cache/apt/*.deb"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by actiononmail on 2013-04-27
Hi All,

I have recently installed Ubuntu 12.10 using Wubi inside Windows 7.All works fine until some fatal error come which results in No Booting of Ubuntu. Somehow, using recovery mode of Ubuntu I have taken backup of all the installed Debian Packages inside **/var/cache/apt/archives** along with other files.

Now after reinstalled all the things once again, I want to reinstall my backup Debian Packages. As a novice, I execute simply "**dpkg -i vlc***" to install VLC Lan Player but got following dependency errors.:(

```

akash@ubuntu:~/apt/archives$ sudo dpkg -i vlc*
Selecting previously unselected package vlc.
(Reading database ... 146582 files and directories currently installed.)
Unpacking vlc (from vlc_2.0.5-0ubuntu0.12.10.1_amd64.deb) ...
Selecting previously unselected package vlc-data.
Unpacking vlc-data (from vlc-data_2.0.5-0ubuntu0.12.10.1_all.deb) ...
Selecting previously unselected package vlc-nox.
Unpacking vlc-nox (from vlc-nox_2.0.5-0ubuntu0.12.10.1_amd64.deb) ...
Selecting previously unselected package vlc-plugin-notify.
Unpacking vlc-plugin-notify (from vlc-plugin-notify_2.0.5-0ubuntu0.12.10.1_amd64.deb) ...
Selecting previously unselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from vlc-plugin-pulse_2.0.5-0ubuntu0.12.10.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libavcodec53 (>= 6:0.8.3-1~) | libavcodec-extra-53 (>= 6:0.8.4); however:
  Package libavcodec53:amd64 is not configured yet.
  Package libavcodec-extra-53 is not installed.
 vlc depends on libavutil51 (>= 6:0.8.3-1~) | libavutil-extra-51 (>= 6:0.8.4); however:
  Package libavutil51:amd64 is not configured yet.
  Package libavutil-extra-51 is not installed.
 vlc depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6:amd64 is not configured yet.
 vlc depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:i386 which provides libgl1 is not configured yet.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.
 vlc depends on libsdl-image1.2 (>= 1.2.10); however:
  Package libsdl-image1.2 is not installed.
 vlc depends on libsdl1.2debian (>= 1.2.11); however:
  Package libsdl1.2debian is not installed.
 vlc 
dpkg: error processing vlc (--install):
 dependency problems - leaving unconfigured
Setting up vlc-data (2.0.5-0ubuntu0.12.10.1) ...
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not configured yet.
 vlc-nox depends on libass4 (>= 0.9.7); however:
  Package libass4:amd64 is not configured yet.
 vlc-nox depends on libavcodec53 (>= 6:0.8.3-1~) | libavcodec-extra-53 (>= 6:0.8.4); however:
  Package libavcodec53:amd64 is not configured yet.
  Package libavcodec-extra-53 is not installed.
 vlc-nox depends on libavformat53 (>= 6:0.8.3-1~) | libavformat-extra-53 (>= 6:0.8.4); however:
  Package libavformat53:amd64 is not configured yet.
  Package libavformat-extra-53 is not installed.
 vlc-nox depends on libavutil51 (>= 6:0.8.3-1~) | libavutil-extra-51 (>= 6:0.8.4); however:
  Package libavutil51:amd64 is not configured yet.
  Package libavutil-extra-51 is not installed.
 vlc-nox depends on libbluray1; however:
  Package libbluray1:amd64 is not configured yet.
 vlc-nox depends on libcddb2; however:
  Package libcddb2 is not configured yet.
 vlc-nox depends on libcrystal
dpkg: error processing vlc-nox (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.0.5-0ubuntu0.12.10.1); however:
  Package vlc-nox is not configured yet.
 vlc-plugin-notify depends on libglib2.0-0 (>= 2.12.0); however:
  Package libglib2.0-0:amd64 is not configured yet.
 vlc-plugin-notify depends on libvlccore5 (>= 2.0.0); however:
  Package libvlccore5 is not installed.

dpkg: error processing vlc-plugin-notify (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.0.5-0ubuntu0.12.10.1); however:
  Package vlc-nox is not configured yet.
 vlc-plugin-pulse depends on libvlccore5 (>= 2.0.0); however:
  Package libvlccore5 is not installed.

dpkg: error processing vlc-plugin-pulse (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 vlc
 vlc-nox
 vlc-plugin-notify
 vlc-plugin-pulse


```

The folder contains all the dependency packages ask by the dpkg but how do I installed them in correct order.So Is it possible to perform complete restore just from the** /var/cache/apt backup**???

Please help

Thanks

---

### Post by oldos2er on 2013-04-28
Try ```
sudo dpkg -i *.deb
```

---

### Post by actiononmail on 2013-05-05
Hi. . i have already one that. And it is due to same command that i got this error

---

