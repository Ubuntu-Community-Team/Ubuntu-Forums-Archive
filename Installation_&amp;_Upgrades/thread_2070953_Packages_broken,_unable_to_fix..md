---
title: "Packages broken, unable to fix."
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by thefitz on 2012-10-14
After installing ia32-libs I keep getting errors and apt-get/ubuntu software center won't work.

The self-repairing on the ubuntu software center does not work.

when I use apt-get install -f
```
root@ubuntu:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  lib32asound2 lib32gcc1 lib32stdc++6 libasound2 libc6-i386 openssh-server
  oss-compat ssh ssh-import-id
Suggested packages:
  lib32asound2-plugins libasound2-python rssh molly-guard openssh-blacklist
  openssh-blacklist-extra monkeysphere
The following packages will be REMOVED:
  appmenu-qt checkbox-qt empathy eog evince evolution-data-server gdb
  ia32-libs jockey-common jockey-gtk libcurl3 libdbusmenu-qt2 libdconf-qt0
  libevince3-3 libexiv2-11 libfolks-eds25 libgexiv2-1 libgl1-mesa-dri
  libpoppler-glib8 libpurple0 libqt4-dbus libqt4-declarative libqt4-network
  libqt4-opengl libqt4-script libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1
  libqtgui4 libsasl2-modules libunity-2d-private0 libv4lconvert0 libvncserver0
  libwmf0.2-7 libwmf0.2-7-gtk nautilus-sendto-empathy nautilus-share ntfs-3g
  python-cupshelpers python-smbc qdbus qt-at-spi remmina remmina-plugin-rdp
  remmina-plugin-vnc samba-common-bin seahorse shotwell smbclient sni-qt
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-gabble telepathy-haze telepathy-salut
  ubuntu-desktop unity-2d unity-2d-panel unity-2d-shell unity-2d-spread vino
  whoopsie xorg
The following NEW packages will be installed:
  openssh-server oss-compat ssh ssh-import-id
The following packages will be upgraded:
  lib32asound2 lib32gcc1 lib32stdc++6 libasound2 libc6-i386
5 upgraded, 4 newly installed, 70 to remove and 3 not upgraded.
10 not fully installed or removed.
Need to get 0 B/5,557 kB of archives.
After this operation, 329 MB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.11.1-0ubuntu7.8); however:
  Version of libc6 on system is 2.15-0ubuntu10.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libc6-i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The following command did not work
```
dpkg-reconfigure -phigh -a
```

Any attempts to purge/auto-remove ia32-libs keeps returning dependency problems.

I am trying to install wine to run .exes, though the issue occurred right after installing ia32-libs.
```
root@ubuntu:~# apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 alsa-utils : Depends: libasound2 (>= 1.0.25)
 bluez-alsa : Depends: libasound2 (>= 1.0.23)
 firefox : Depends: libasound2 (>= 1.0.23)
 gstreamer0.10-alsa : Depends: libasound2 (>= 1.0.23)
 ia32-libs : Depends: lib32bz2-1.0 but it is not going to be installed
 lib32gcc1 : Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) but it is not going to be installed
 lib32stdc++6 : Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) but it is not going to be installed
 libasound2 : Depends: libpython2.6 (>= 2.6) but it is not installable
 libasound2-plugins : Depends: libasound2 (>= 1.0.25)
 libc6-i386 : Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.15-0ubuntu10 is to be installed
 libcanberra0 : Depends: libasound2 (>= 1.0.23)
 libfreerdp-plugins-standard : Depends: libasound2 (>= 1.0.23)
 libportaudio2 : Depends: libasound2 (> 1.0.24.1)
 libsdl1.2debian : Depends: libasound2 (> 1.0.24.1)
 libv4lconvert0 : Breaks: libv4l-0 (< 0.8.5-4) but 0.6.4-1ubuntu1 is to be installed
 libvisual-0.4-plugins : Depends: libasound2 (>= 1.0.23)
 pulseaudio : Depends: libasound2 (>= 1.0.24.1)
 speech-dispatcher : Depends: libasound2 (> 1.0.24.1)
 thunderbird : Depends: libasound2 (>= 1.0.23)
 wine1.4 : Depends: libgettextpo0 but it is not going to be installed
           Depends: wine1.4-amd64 (= 1.4-0ubuntu4) but it is not going to be installed
           Depends: binfmt-support (>= 1.1.2)
           Depends: wine1.4-i386 (= 1.4-0ubuntu4)
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind
           Recommends: winetricks but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

If anyone could help I would really appreciate it.
Looking at it, it looks like the ia32-libs version is too low, I have no clue how to do anything about it because uninstalling/installing is broken.

---

### Post by dino99 on 2012-10-14
wine 1.4 is outdated, use the latest from ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

and you might need to install ia32-libs-multiarch (look at details via synaptic)

sudo apt-get install synaptic
sudo synaptic

on which ubuntu are you trying the upgrade ?

note: you should not be logged as root, its dangerous.

---

### Post by thefitz on 2012-10-14
> **dino99 said:**
> 
sudo apt-get install synaptic
sudo synaptic


```
root@ubuntu:~# sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 alsa-utils : Depends: libasound2 (>= 1.0.25)
 bluez-alsa : Depends: libasound2 (>= 1.0.23)
 firefox : Depends: libasound2 (>= 1.0.23)
 gstreamer0.10-alsa : Depends: libasound2 (>= 1.0.23)
 ia32-libs : Depends: lib32bz2-1.0 but it is not going to be installed
 lib32gcc1 : Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) but it is not going to be installed
 lib32stdc++6 : Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) but it is not going to be installed
 libasound2 : Depends: libpython2.6 (>= 2.6) but it is not installable
 libasound2-plugins : Depends: libasound2 (>= 1.0.25)
 libc6-i386 : Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.15-0ubuntu10 is to be installed
 libcanberra0 : Depends: libasound2 (>= 1.0.23)
 libfreerdp-plugins-standard : Depends: libasound2 (>= 1.0.23)
 libportaudio2 : Depends: libasound2 (> 1.0.24.1)
 libsdl1.2debian : Depends: libasound2 (> 1.0.24.1)
 libv4lconvert0 : Breaks: libv4l-0 (< 0.8.5-4) but 0.6.4-1ubuntu1 is to be installed
 libvisual-0.4-plugins : Depends: libasound2 (>= 1.0.23)
 pulseaudio : Depends: libasound2 (>= 1.0.24.1)
 speech-dispatcher : Depends: libasound2 (> 1.0.24.1)
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
 thunderbird : Depends: libasound2 (>= 1.0.23)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

> **dino99 said:**
> 
note: you should not be logged as root, its dangerous.
Same errors out of root, I logged into root hoping that not having to sudo it would fix it (Three days looking for an answer, its happened both times I have reinstalled ubuntu, got desperate).

> **dino99 said:**
> wine 1.4 is outdated, use the latest from ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

and you might need to install ia32-libs-multiarch (look at details via synaptic)

on which ubuntu are you trying the upgrade ?


I read somewhere 1.5 was still beta, the latest stable was 1.4, I'll check out the link, thanks.

I cant install anything, thats the problem.

I am using Ubuntu 12.04

---

### Post by nirux3233 on 2013-03-19
hey try this out...here I am installng wine..

Open Terminal




[code and its reasoning will be in the description]

1)sudo apt-get install -f
2)sudo apt-get autoremove
3)sudo apt-get update
4)sudo add-apt-repository ppa:ubuntu-wine/ppa
5)sudo apt-get update
6)sudo dpkg --add-architecture i386     //the dependencies error)
7)sudo apt-get update
8)sudo apt-get install wine     //this step will take about 4-7 minutes 
DONE!!!..

It really works...

P.S
source - [www.youtube.com/watch?v=RxddQYJSxog](www.youtube.com/watch?v=RxddQYJSxog)

---

