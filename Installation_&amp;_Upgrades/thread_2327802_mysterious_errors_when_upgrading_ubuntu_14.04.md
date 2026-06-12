---
title: "mysterious errors when upgrading ubuntu 14.04"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2016-06-14
Dear Fellows

I have ubuntu 14.04 installed on my system. Recently, when I try to run the command

```
sudo apt-get update
```

The following error appears at the terminal:```
Errors were encountered while processing:
 /var/cache/apt/archives/lsb-release_4.1+Debian11ubuntu6.1_all.deb
 /var/cache/apt/archives/apport_2.14.1-0ubuntu3.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I tried similar commands such as

```
sudo apt-get -f install
``` with no packages. However, the same error appears on the terminal


I tried the command:  ```
grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/*


```

and this is the output:

```
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb http://www.openfoam.org/download/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
grep: /etc/apt/sources.list.d/*: No such file or directory


```


would some body please hint me how can I fix this error?


  Regards

---

### Post by babakflame on 2016-06-14
I used the following command:

```
sudo rm /etc/apt/sources.list


```

Nothing happened. After that, I typed:

```
sudo software-properties-gtk


```

The is the output:

```
WARNING:root:could not open file '/etc/apt/sources.list'

```

found these command in the net. Seems did not work for me.

  Regards

---

### Post by Omar_Jair on 2016-06-14
It's because you deleted the sources.list file, you have to generate a new one, sadly i cannot give you a link but here is what i have on a clean ubuntu install
> # deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

---

### Post by babakflame on 2016-06-14
Thanks Omar

However, your comments did not help me bro. :(

---

### Post by QIII on 2016-06-14
Hello!

What do you mean when you say Omar_Jair's post did not help?

---

### Post by babakflame on 2016-06-14
Hello Qill

  I copied the sources.list Omar sent me on my sources.list file. However, after running
```
 sudo apt-get update
```

I receive the following error this time:
```

Fetched 1,146 kB in 10s (114 kB/s)                                             
Reading package lists... Done
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin'
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
W: Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
W: Ignoring Provides line with DepCompareOp for package php-seclib
W: Ignoring Provides line with DepCompareOp for package php-sabre-http
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: You may want to run apt-get update to correct these problems



```

I tried ```
 sudo apt-get update 
``` several times. however, the same error appears.


I still receive this error as well:


```
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_16.01+16.04.20160420_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ajgreeny on 2016-06-14
You can easily create a new sources.list file by using the [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/) site which allows you t6o set the specific ubuntu repos you want to use along with many of the "Other software" third party and ppa repos.

Run it to produce the new file then replace your old file, if you actually have one, with this new one.

Finally run ```
sudo apt-get update
``` and show us the output, or if you're happy with the way it goes just carry on and update.

---

### Post by deadflowr on 2016-06-14
^^^On top of using the repogen site to make a new sources.list, I'd run
```
sudo apt-get clean
```
to purge the cache directory.
Start it out fresh

---

### Post by babakflame on 2016-06-14
Dear Fellows

  Many thanks for your replies. I used the link : [https://repogen.simplylinux.ch](https://repogen.simplylinux.ch) to create a new sources.list. then I replaced it with /etc/apt/sources.list file

The ```
sudo apt-get update
```

works without any problem. Then I tried the following installation:
```
sudo apt-get install 
python python-dev
```

The output is as:
```
The following packages have unmet dependencies:
 console-setup : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 console-setup-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 cups-daemon : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
               Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 dbus : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 dpkg : Breaks: software-center (< 13.10-0ubuntu9~) but 13.10-0ubuntu4.1 is to be installed
 glib-networking : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 glib-networking-services : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 initscripts : Depends: sysvinit-utils (>= 2.88dsf-50)
 keyboard-configuration : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 libarchive13 : Depends: libnettle4 (>= 2.3) but it is not going to be installed
 libc-dev-bin : Depends: libc6 (< 2.20) but 2.23-0ubuntu3 is to be installed
 libc6-dbg : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is to be installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is to be installed
 libgnutls28 : Depends: libhogweed2 (>= 2.7) but it is not going to be installed
               Depends: libnettle4 (>= 2.7) but it is not going to be installed
 libncurses5 : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 libncurses5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 libncursesw5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
                    Depends: libncursesw5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 liboxideqt-qmlplugin : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 liboxideqtcore0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 liboxideqtquick0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 libproxy-tools : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 libqt5dbus5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
               Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5gui5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
              Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5network5 : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
                  Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                  Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5quick5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is to be installed
                Depends: qtbase-abi-5-5-1 but it is not installable
                Depends: qtdeclarative-abi-5-5-0 but it is not installable
 libreoffice-avmedia-backend-gstreamer : Depends: libreoffice-core but it is not going to be installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-calc : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-ogltrans : Depends: libreoffice-core but it is not going to be installed
 libreoffice-pdfimport : Depends: libreoffice-core but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libtinfo-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 mythes-en-us : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 qml-module-qt-labs-folderlistmodel : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 qml-module-qt-labs-settings : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 qml-module-qtquick-dialogs : Depends: qml-module-qtquick-privatewidgets but it is not installable
                              Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-layouts : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-localstorage : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                                   Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is to be installed
                                   Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-window2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 ufw : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
       Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 ureadahead : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
 util-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
              Depends: sysvinit-utils (>= 2.88dsf-59.1~)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

I tried ```
sudo apt-get -f install 
```

this is the output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 console-setup : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 console-setup-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 cups-daemon : Depends: init-system-helpers (>= 1.18~) but 1.14 is installed
               Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 dbus : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 dpkg : Breaks: software-center (< 13.10-0ubuntu9~) but 13.10-0ubuntu4.1 is installed
 glib-networking : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 glib-networking-services : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 initscripts : Depends: sysvinit-utils (>= 2.88dsf-50)
 keyboard-configuration : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 libarchive13 : Depends: libnettle4 (>= 2.3) but it is not installed
 libc-dev-bin : Depends: libc6 (< 2.20) but 2.23-0ubuntu3 is installed
 libc6-dbg : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is installed
 libgnutls28 : Depends: libhogweed2 (>= 2.7) but it is not installed
               Depends: libnettle4 (>= 2.7) but it is not installed
 libncurses5 : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is installed
 libncurses5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is installed
 libncursesw5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is installed
                    Depends: libncursesw5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is installed
 liboxideqt-qmlplugin : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
 liboxideqtcore0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
 liboxideqtquick0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
 libproxy-tools : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 libqt5dbus5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is installed
               Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5gui5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is installed
              Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5network5 : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
                  Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is installed
                  Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5quick5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is installed
                Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is installed
                Depends: qtbase-abi-5-5-1 but it is not installable
                Depends: qtdeclarative-abi-5-5-0 but it is not installable
 libreoffice-avmedia-backend-gstreamer : Depends: libreoffice-core but it is not installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-calc : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-draw : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-impress : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-math : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libreoffice-ogltrans : Depends: libreoffice-core but it is not installed
 libreoffice-pdfimport : Depends: libreoffice-core but it is not installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 libtinfo-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is installed
 mythes-en-us : Depends: libreoffice-core but it is not installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not installed
 qml-module-qt-labs-folderlistmodel : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
 qml-module-qt-labs-settings : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
 qml-module-qtquick-dialogs : Depends: qml-module-qtquick-privatewidgets but it is not installable
                              Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-layouts : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-localstorage : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is installed
                                   Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is installed
                                   Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-window2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 ufw : Depends: init-system-helpers (>= 1.18~) but 1.14 is installed
       Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
 ureadahead : Depends: init-system-helpers (>= 1.18~) but 1.14 is installed
 util-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is installed
              Depends: sysvinit-utils (>= 2.88dsf-59.1~)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


```

Any help is appreciated.

---

### Post by kansasnoob on 2016-06-14
> I copied the sources.list Omar sent me on my sources.list file.

Omar posted a Xenial sources.list but you were running Trusty so things are probably downright hosed now :(

Start by posting the full output of:

```
cat /etc/apt/sources.list
```

And:

```
ls /etc/apt/sources.list.d
```

If you now have a mix of Trusty and Xenial packages I'd put very low odds on recovering from this so before trying anything else I'd create a full backup of anything important in case you have to reinstall.

---

### Post by ajgreeny on 2016-06-14
OK, so now let's see the output of ```
cat /etc/apt/sources.list
```making sure you copy the whole output, not just the part that shows in the terminal to see if you accidentally m,issed something.
Alternatively just copy that file to your home, rename it as sources.txt and attach the renamed file using the paperclip icon in the Advanced reply toolbar

---

### Post by babakflame on 2016-06-14
Hi

 This is the output of ```
cat /etc/apt/sources.list
```  :  ```

#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main universe 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main universe 
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-security main universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main universe 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner 
```


Then I ran ```
ls /etc/apt/sources.list.d
```

I think the second command lists directory contents. Nothing was there.

---

### Post by deadflowr on 2016-06-14
Perhaps also a sample of a package's version to see where things might be coming from:
Something like:
```
apt-cache policy console-setup
```
since that was the first one listed causing depends errors.

Here's the default for 14.04:
```
console-setup:
  Installed: 1.70ubuntu8
  Candidate: 1.70ubuntu8
  Version table:
 *** 1.70ubuntu8 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by babakflame on 2016-06-14
This is the output of ```
sudo apt-cache policy console-setup
```

```


console-setup:
  Installed: 1.108ubuntu15
  Candidate: 1.108ubuntu15
  Version table:
 *** 1.108ubuntu15 0
        100 /var/lib/dpkg/status
     1.70ubuntu8 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

---

### Post by deadflowr on 2016-06-14
You probably need to re-add the openfoam repo, since the sources.list file is missing it now.

---

### Post by babakflame on 2016-06-14
Thanks deadflowr

Just onething can u explain these errors to me:

```


babak@babak-VirtualBox:~$ sudo apt-get install git-core build-essential flex bison zlib1g-dev qt4-dev-tools libqt4-dev gnuplot libreadline-dev \
> libncurses-dev libxt-dev libopenmpi-dev openmpi-bin libboost-system-dev libboost-thread-dev libgmp-dev libmpfr-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libncurses5-dev' instead of 'libncurses-dev'
bison is already the newest version.
build-essential is already the newest version.
flex is already the newest version.
libboost-system-dev is already the newest version.
libboost-thread-dev is already the newest version.
libmpfr-dev is already the newest version.
libncurses5-dev is already the newest version.
libreadline-dev is already the newest version.
libxt-dev is already the newest version.
zlib1g-dev is already the newest version.
gnuplot is already the newest version.
libopenmpi-dev is already the newest version.
openmpi-bin is already the newest version.
git-core is already the newest version.
libqt4-dev is already the newest version.
qt4-dev-tools is already the newest version.
libgmp-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 console-setup : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 console-setup-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 cups-daemon : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
               Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 dbus : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 dpkg : Breaks: software-center (< 13.10-0ubuntu9~) but 13.10-0ubuntu4.1 is to be installed
 glib-networking : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 glib-networking-services : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 initscripts : Depends: sysvinit-utils (>= 2.88dsf-50)
 keyboard-configuration : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 libarchive13 : Depends: libnettle4 (>= 2.3) but it is not going to be installed
 libc-dev-bin : Depends: libc6 (< 2.20) but 2.23-0ubuntu3 is to be installed
 libc6-dbg : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is to be installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.7) but 2.23-0ubuntu3 is to be installed
 libgnutls28 : Depends: libhogweed2 (>= 2.7) but it is not going to be installed
               Depends: libnettle4 (>= 2.7) but it is not going to be installed
 libncurses5 : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 libncurses5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 libncursesw5-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
                    Depends: libncursesw5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 liboxideqt-qmlplugin : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 liboxideqtcore0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 liboxideqtquick0 : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 libproxy-tools : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
 libqt5dbus5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
               Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5gui5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
              Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5network5 : Depends: libproxy1v5 (>= 0.4.11) but it is not installable
                  Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                  Depends: qtbase-abi-5-5-1 but it is not installable
 libqt5quick5 : Depends: libqt5core5a (>= 5.5.1) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is to be installed
                Depends: qtbase-abi-5-5-1 but it is not installable
                Depends: qtdeclarative-abi-5-5-0 but it is not installable
 libreoffice-avmedia-backend-gstreamer : Depends: libreoffice-core but it is not going to be installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-calc : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libreoffice-ogltrans : Depends: libreoffice-core but it is not going to be installed
 libreoffice-pdfimport : Depends: libreoffice-core but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 libtinfo-dev : Depends: libtinfo5 (= 5.9+20140118-1ubuntu1) but 6.0+20160213-1ubuntu1 is to be installed
 mythes-en-us : Depends: libreoffice-core but it is not going to be installed or
                         openoffice.org-core (>= 1.9) but it is not installable or
                         language-support-writing-en but it is not installable
 python3-uno : Depends: libreoffice-core (= 1:4.2.8-0ubuntu4) but it is not going to be installed
 qml-module-qt-labs-folderlistmodel : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 qml-module-qt-labs-settings : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
 qml-module-qtquick-dialogs : Depends: qml-module-qtquick-privatewidgets but it is not installable
                              Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-layouts : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                              Depends: qtbase-abi-5-5-1 but it is not installable
                              Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-localstorage : Depends: libqt5core5a (>= 5.5.0) but 5.2.1+dfsg-1ubuntu14.3 is to be installed
                                   Depends: libqt5qml5 (>= 5.5.1) but 5.2.1-3ubuntu15.1 is to be installed
                                   Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick-window2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 qml-module-qtquick2 : Depends: qtdeclarative-abi-5-5-0 but it is not installable
 ufw : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
       Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
 ureadahead : Depends: init-system-helpers (>= 1.18~) but 1.14 is to be installed
 util-linux : Depends: lsb-base (>= 4.1+Debian11ubuntu7) but 4.1+Debian11ubuntu6.1 is to be installed
              Depends: sysvinit-utils (>= 2.88dsf-59.1~)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




```

---

### Post by deadflowr on 2016-06-14
To try to simplify it, newer packages need newer dependencies.
Example, console-setup installed is newer than console-setup from the repos.
it requires lsb-base that is higher than the version you are pulling from the repos.
So then the package installation complains about, and so on and so on.

I'm guessing about needing to re-add the openfoam repo as that was the one repo the seemed to differ from the old and new sources.lists.
I do not even know if said newer versions of packages are even in that repo, as we do not know if there was any other repos that you had previously added and then removed.
But based on the information so far, and it being as accurate as can be, the openfoam repo seems to be where those packages come from.
If any of that makes sense.

---

### Post by ajgreeny on 2016-06-14
I see you are also missing the **multiverse** repos which may be needed for some of those packages that are missing.

---

### Post by babakflame on 2016-06-14
Many thanks Deadflowr and ajgreeny


**Suddenly my Terminal disappeared and then when I log in to ubuntu;  it logs out immediately**. Can you please help me to resolve this new problem? :confused::confused::confused::confused::confused:

 I did not do any thing, AFA I know.


  Help me Guys. I lost my access to ubuntu. I have lots of imporatnt files in it.

---

### Post by babakflame on 2016-06-14
Dear Fellows

   When I log in to the system. It appears:


[HTML]system program problem detected[/HTML]

after some seconds, it logs out and returns to the initial page asking for pass word to log in.


   This is the worst problem I had so far with ubuntu.
I tried ```
killall -u babak
``` to kill all the process in the text mode ```
ctrl+alt+F5
```. 
  
Although it might not have any relation to the above problem, however, my system is an iMac wich I used virtualBox to install ubuntu 14.04 on it.

---

