---
title: "Issues installing/upgrading via apt-get"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by wallace3 on 2014-09-25
I have been trying to update from 12.04 and keep running into issues where the system cannot fix dependencies. I have tried and apt-get -f install, I have remade my repo lists.  I can't seem to figure out what is going on here.  Anyone have an idea?

```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aptdaemon : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu7) but 1.1.1-1ubuntu5 is installed
 compiz-plugins : Depends: compiz-core (= 1:0.9.7.12-0ubuntu1) but 1:0.9.11.2+14.04.20140714-0ubuntu1 is installed
 compiz-plugins-default : Depends: compiz-core (= 1:0.9.7.12-0ubuntu1) but 1:0.9.11.2+14.04.20140714-0ubuntu1 is installed
 compiz-plugins-main : Depends: compiz-core-abiversion-20120305
 compiz-plugins-main-default : Depends: compiz-core-abiversion-20120305
 dconf-tools : Depends: dconf-editor but it is not installable
 eog : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 gdm : Depends: libaudit1 (>= 1:2.2.1) but it is not installable
       Depends: libgdm1 (= 3.10.0.1-0ubuntu3) but it is not installable
       Depends: libsystemd-daemon0 (>= 31) but it is not installable
       Depends: libsystemd-login0 (>= 186) but it is not installable
       Depends: sysv-rc (>= 2.88dsf-24) but 2.88dsf-13.10ubuntu11.1 is installed or
                file-rc (>= 0.8.16) but it is not installable
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3) but it is not installable
       Depends: libpam-systemd but it is not installable
       Depends: gnome-session-bin (>= 3.6) but 3.2.1-0ubuntu8 is installed
       Depends: libglib2.0-bin (>= 2.35.0) but 2.32.3-0ubuntu1 is installed
       Depends: dconf-gsettings-backend (>= 0.12.1-2) but 0.12.0-0ubuntu1.1 is installed
       Recommends: xserver-xephyr but it is not installed
       Recommends: xserver-xorg
 gnome-contacts : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 gnome-control-center : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 gnome-panel : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 gnome-screensaver : Depends: libsystemd-login0 (>= 31) but it is not installable
 gnome-settings-daemon : Depends: libgnome-desktop-3-2 (>= 3.3.4) but it is not installed
 gnome-shell : Depends: gir1.2-clutter-1.0 (>= 1.11.11) but 1.10.6-1~precise1 is installed
               Depends: gir1.2-glib-2.0 (>= 1.37) but 1.32.0-1 is installed
               Depends: gir1.2-gtk-3.0 (>= 3.8) but 3.4.2-0ubuntu0.5 is installed
               Depends: gir1.2-mutter-3.0 (>= 3.10.0) but 3.4.1-0ubuntu1 is installed
               Depends: gir1.2-soup-2.4 (>= 2.40.1) but 2.38.1-1 is installed
               Depends: libclutter-1.0-0 (>= 1.13.4) but 1.10.6-1~precise1 is installed
               Depends: libcogl-pango15 (>= 1.15.8) but it is not installable
               Depends: libcogl15 (>= 1.15.8) but it is not installable
               Depends: libecal-1.2-16 (>= 3.5.91) but it is not installable
               Depends: libedataserver-1.2-18 (>= 3.5.91) but it is not installable
               Depends: libgcr-base-3-1 (>= 3.8.0) but it is not installable
               Depends: libgjs0-libmozjs-24-0 but it is not installable
               Depends: libgjs0e (>= 1.40.1) but it is not installable
               Depends: libical1 (>= 1.0) but it is not installable
               Depends: libmozjs-24-0 but it is not installable
               Depends: libmutter0c (>= 3.10) but it is not installable
               Depends: libmutter0c (< 3.11) but it is not installable
               Depends: libsecret-1-0 (>= 0.7) but it is not installable
               Depends: evolution-data-server (>= 3.7.90) but 3.2.3-0ubuntu7 is installed
               Depends: gir1.2-gdm-1.0 but it is not installable
               Depends: gir1.2-atspi-2.0 (>= 2.9.91) but 2.4.2-0ubuntu0.1 is installed
               Depends: gir1.2-caribou-1.0 (>= 0.4.8) but 0.4.2-1ubuntu1 is installed
               Depends: gir1.2-gcr-3 (>= 3.7.5) but it is not installable
               Depends: gir1.2-gnomebluetooth-1.0 (>= 3.6.0) but 3.2.2-0ubuntu5 is installed
               Depends: gir1.2-gnomedesktop-3.0 (>= 3.7.90) but it is not installed
               Depends: gir1.2-ibus-1.0 (>= 1.5.2) but it is not installed
               Depends: gir1.2-nmgtk-1.0 (>= 0.9.8) but it is not installable
               Depends: gir1.2-telepathylogger-0.2 (>= 0.8.0) but 0.4.0-0ubuntu1 is installed
               Depends: gjs (>= 1.37.4) but 1.32.0-1ubuntu1 is installed
               Depends: gnome-shell-common (= 3.10.4-0ubuntu5.2) but 3.4.1-0ubuntu2 is installed
               Recommends: gkbd-capplet but it is not installed
 gnome-themes-standard : Depends: gnome-themes-standard-data (= 3.10.0-1ubuntu2) but it is not installable
 gtk2-engines-pixbuf : Depends: libgtk2.0-0 (= 2.24.10-0ubuntu6) but 2.24.23-0ubuntu1.1 is installed
 libcompizconfig0 : Depends: compiz-core-abiversion-20120305
 libevolution : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 libgail-3-0 : Depends: libgtk-3-0 (= 3.4.2-0ubuntu0.5) but 3.10.8-0ubuntu1.2 is installed
 libgail18 : Depends: libgtk2.0-0 (= 2.24.10-0ubuntu6) but 2.24.23-0ubuntu1.1 is installed
 libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 10.1.3-0ubuntu0.1)
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.32.3-0ubuntu1) but 2.40.0-2 is installed
 libgtk-3-bin : Depends: libgtk-3-common (= 3.4.2-0ubuntu0.5) but 3.10.8-0ubuntu1.2 is installed
 libpango1.0-0 : Depends: libpangoxft-1.0-0 (= 1.36.3-1ubuntu1) but it is not installable
                 Depends: libpangox-1.0-0 (>= 0.0.2-2~) but it is not installable
 libunity-core-5.0-5 : Depends: unity-services (= 5.18.0-0ubuntu2) but 7.2.2+14.04.20140714-0ubuntu1.1 is installed
 libxfixes-dev : Depends: libxfixes3 (= 1:5.0-4ubuntu4) but 1:5.0.1-1ubuntu1 is installed
 nautilus : Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not installed
 plymouth : Depends: libplymouth2 (= 0.8.8-0ubuntu17) but 0.8.2-2ubuntu31 is installed
            Depends: upstart (>= 1.11-0ubuntu3) but 1.5-0ubuntu7.2 is installed
            Depends: sysv-rc (>= 2.88dsf-24) but 2.88dsf-13.10ubuntu11.1 is installed or
                     file-rc (>= 0.8.16) but it is not installable
 plymouth-label : Depends: plymouth (= 0.8.2-2ubuntu31) but 0.8.8-0ubuntu17 is installed
 python-aptdaemon : Depends: python-apt (>= 0.8.5~ubuntu1) but 0.8.3ubuntu7 is installed
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu7) but 1.1.1-1ubuntu5 is installed
 python-aptdaemon.gtkwidgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu7) but 1.1.1-1ubuntu5 is installed
 python-aptdaemon.pkcompat : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu7) but 1.1.1-1ubuntu5 is installed
 python-gi : Depends: libgirepository-1.0-1 (>= 1.33.10) but 1.32.0-1 is installed
             Depends: gir1.2-glib-2.0 (>= 1.35.9) but 1.32.0-1 is installed
 python-gi-cairo : Depends: python-gi (= 3.2.2-1~precise) but 3.12.0-1ubuntu1 is installed
 software-center : Depends: python-lxml but it is not installed
                   Recommends: xz-utils (>= 5.1.1alpha+20120614-1) but 5.1.1alpha+20110809-3 is installed
 unity-lens-applications : Depends: unity-common (>= 4.4.0)
E: Unmet dependencies. Try using -f.
```

---

### Post by deadflowr on 2014-09-25
[COLOR=#000000] > I have remade my repo lists[/COLOR]

What does that mean?
An explanation would be helpful.
(I don't mean to be snide, just wondering...)

Also, please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") when posting outputs like the above.

---

### Post by wallace3 on 2014-09-25
Sorry.  I ment I removed the repo list and updated it with the current links for the repository's.

---

### Post by deadflowr on 2014-09-25
> **wallace3 said:**
> Sorry.  I ment I removed the repo list and updated it with the current links for the repository's.
 Okay, please post the output from
```
cat /etc/apt/sources.list
and
ls /etc/apt/sources.list/d/
```
The first will show the default repos, and second any 3rd party repos you may have added at some point in time.
Also the output for
```
sudo apt-get update
```
for simple clarity on all things.

---

### Post by wallace3 on 2014-09-25
Thanks for the help.

cat /etc/apt/sources.list


```
#############################################################
###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe
###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main universe
###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

```

ls /etc/apt/sources.list/d/
```
ls: cannot access /etc/apt/sources.list/d/: Not a directory

```

sudo apt-get update
```
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [50.7 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [98.7 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [98.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [110 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources [32.7 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [457 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [104 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [478 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [110 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [867 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [255 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Sources [16.2 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Sources [5,551 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [181 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [21.2 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex [3,564 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en [54.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,954 kB in 25s (117 kB/s)
Reading package lists... Done

```

---

### Post by ian-weisser on 2014-09-25
> **wallace3 said:**
> I have been trying to update from 12.04 and keep running into issues where the system cannot fix dependencies.

```

The following packages have unmet dependencies:
 aptdaemon : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu7) but 1.1.1-1ubuntu5 is installed

```

```
#############################################################
###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main universe
```

It looks like you are trying to upgrade from 12.04 to 14.04.

The first big problem is that you are still using 12.04 (precise) repositories instead of 14.04 (trusty).

If you are *not* trying to upgrade to 14.04...well you have done so:
```
~$ rmadison -u ubuntu python-aptdaemon
 python-aptdaemon | 0.43+bzr805-0ubuntu9   | precise-updates  | all
 python-aptdaemon | 1.1.1-1ubuntu5.1       | trusty-updates   | all
```

So you are running with 14.04 packages.
Most of your error messages indicate that you are trying to replace a current package version with a much older version.
Change your sources from precise to trusty, and most of those problems should be solved.

---

### Post by wallace3 on 2014-09-25
Awesome that did it thank you so very much.

---

