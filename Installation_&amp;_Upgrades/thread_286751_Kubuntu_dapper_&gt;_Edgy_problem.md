---
title: "Kubuntu dapper &gt; Edgy problem"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by greew on 2006-10-28
I've tried to update my kde dapper to edgy. First switching all 

```
sudo apt-get update && sudo apt-get -f dist-upgrade && sudo apt-get dist-upgrade

```

and then I get

```
eading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  comerr-dev kdelibs-data kdelibs4c2a launchpad-integration libavahi-client3 libcupsys2 libcupsys2-dev libdbus-1-3 libgcrypt11 libgcrypt11-dev libglib2.0-dev libgnutls-dev libgnutls13
  libgpg-error-dev libgpg-error0 libgtk2.0-0 libgtk2.0-bin libkadm55 libkrb5-dev liblua50 liblualib50 liblzo-dev libmysqlclient15-dev libmysqlclient15off libopencdk8 libopencdk8-dev libpango1.0-0
  libpango1.0-common libpopt-dev libpopt0 libpq-dev libpq4 libqt3-headers libqt3-mt libqt3-mt-dev libqt4-core libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql libsqlite0-dev libssl-dev
  libtasn1-3 libtasn1-3-dev libxft-dev libxft2 libxslt1.1 mysql-common qt3-dev-tools x11-common xbase-clients xutils xutils-dev
Suggested packages:
  cupsys-common rng-tools libgcrypt11-doc libglib2.0-doc gnutls-doc gnutls-bin krb5-doc ttf-kochi-gothic ttf-kochi-mincho ttf-thryomanes ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp postgresql-doc-8.1 libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libqt3-i18n qt3-doc qt4-doc sqlite-doc
Recommended packages:
  libgnome2-0 x-ttcidfont-conf libgl1-mesa-glx libgl1 libqt3-compat-headers qt4-qtconfig libtasn1-3-bin
The following packages will be REMOVED:
  kdelibs-bin libqt4-debug-dev
The following NEW packages will be installed:
  comerr-dev launchpad-integration libcupsys2-dev libdbus-1-3 libgcrypt11-dev libglib2.0-dev libgnutls-dev libgnutls13 libgpg-error-dev libkadm55 libkrb5-dev liblua50 liblualib50 liblzo-dev
  libmysqlclient15-dev libopencdk8-dev libpopt-dev libpq-dev libsqlite0-dev libssl-dev libtasn1-3 libtasn1-3-dev libxft-dev xbase-clients xutils xutils-dev
The following packages will be upgraded:
  kdelibs-data kdelibs4c2a libavahi-client3 libcupsys2 libgcrypt11 libgpg-error0 libgtk2.0-0 libgtk2.0-bin libmysqlclient15off libopencdk8 libpango1.0-0 libpango1.0-common libpopt0 libpq4
  libqt3-headers libqt3-mt libqt3-mt-dev libqt4-core libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql libxft2 libxslt1.1 mysql-common qt3-dev-tools x11-common
27 upgraded, 26 newly installed, 2 to remove and 769 not upgraded.
12 not fully installed or removed.
Need to get 0B/52.3MB of archives.
After unpacking 51.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 106050 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package fglrx-6-8-0
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
greew@greewie:~$         

```

I'm quite new to linux in general and have tried quite a few things to get this to work, eg. the following commands

```

sudo apt-get -f install
sudo apt-get -f dist-upgrade
sudo dpkg --configure -a

```

but none of these helps me out. No mather what I do with apt, I get errors.

Can anyone see what the problem here is and - hopefully - how I'm able to get my apt back to work.

Regards
Jesper

---

### Post by greew on 2006-10-28
I found the solution - or rather - another helpful person did:

[http://www.ubuntuforums.org/showthread.php?t=286351](http://www.ubuntuforums.org/showthread.php?t=286351)

---

