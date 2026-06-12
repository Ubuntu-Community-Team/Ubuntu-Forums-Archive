---
title: "apt-get, aptitude, etc. - all hanging during unpacking"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by Hammi on 2014-09-20
Hi - I'm trying to install a new program, owncloud from ownclouds repositories, under Ubuntu 14.04, as described on [http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud)

I've tried installing through apt-get, aptitude, and even installing the package with dpkg manually - nothing helps, it always hangs at "unpacking" with a blinking cursor. I have to close the terminal, then kill dpkg, then run

```
dpkg --configure -a
```

and then can start again.

What can I do to make apt-get or aptitude produce a meaningful error? As it's just "hanging" with a blinking cursor, I don't know what to fix. Even

```
aptitude -v -v -v install owncloud
```

just leads to a blinking cursor after unpacking with no error.

Help, please!

---

### Post by QIII on 2014-09-20
Hello!

Is it hanging consistently at one package?  If so, what is it?

Do you use any PPAs?  If so, which ones?

Could you please post a screenshot?  Don't cut & paste the image. Please use the attachment feature by clicking the paperclip icon above the text entry box.

Cheers!

---

### Post by Hammi on 2014-09-28
Yes, it only happens when I try to install one specific package, owncloud 7, from the official repo. Steps to install, as per the owncloud documentation:

```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/ /' >> /etc/apt/sources.list.d/owncloud.list"
wget http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key
sudo apt-key add - < Release.key
sudo apt-get update
sudo apt-get install owncloud

```

I know, questions about this specific package are surely better positioned within the owncloud community. I'm trying to understand how to debug apt-get (or dpkg -i) under Ubuntu in this case.

"Screenshot" from installing:

```
root@[mymachine]:/home/[myhome]# sudo apt-get install owncloud
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  ghostscript gsfonts imagemagick-common libcupsfilters1 libcupsimage2
  libfftw3-double3 libgs9 libgs9-common libicu52 libijs-0.35 libjasper1
  libjbig2dec0 liblcms2-2 liblqr-1-0 libmagickcore5 libmagickwand5 libopts25
  libpaper-utils libpaper1 ntp php-xml-parser php5-curl php5-imagick php5-intl
  php5-pgsql php5-sqlite poppler-data
Vorgeschlagene Pakete:
  ghostscript-x hpijs libfftw3-bin libfftw3-dev fonts-droid libjasper-runtime
  liblcms2-utils libmagickcore5-extra ntp-doc libav-tools ffmpeg
  libreoffice-writer poppler-utils fonts-japanese-mincho fonts-ipafont-mincho
  fonts-japanese-gothic fonts-ipafont-gothic fonts-arphic-ukai
  fonts-arphic-uming fonts-unfonts-core
Empfohlene Pakete:
  php5-apc
Die folgenden NEUEN Pakete werden installiert:
  ghostscript gsfonts imagemagick-common libcupsfilters1 libcupsimage2
  libfftw3-double3 libgs9 libgs9-common libicu52 libijs-0.35 libjasper1
  libjbig2dec0 liblcms2-2 liblqr-1-0 libmagickcore5 libmagickwand5 libopts25
  libpaper-utils libpaper1 ntp owncloud php-xml-parser php5-curl php5-imagick
  php5-intl php5-pgsql php5-sqlite poppler-data
0 aktualisiert, 28 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 42,9 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 183 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen: 1 http://de.archive.ubuntu.com/ubuntu/ trusty/main imagemagick-common all 8:6.7.7.10-6ubuntu3 [37,2 kB]
Holen: 2 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupsfilters1 amd64 1.0.52-0ubuntu1.2 [74,4 kB]
Holen: 3 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupsimage2 amd64 1.7.2-0ubuntu1.2 [15,3 kB]
Holen: 4 http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/  owncloud 7.0.2-1 [23,3 MB]
Holen: 5 http://de.archive.ubuntu.com/ubuntu/ trusty/main libfftw3-double3 amd64 3.3.3-7ubuntu3 [702 kB]
Holen: 6 http://de.archive.ubuntu.com/ubuntu/ trusty/main libicu52 amd64 52.1-3 [6.770 kB]
Holen: 7 http://de.archive.ubuntu.com/ubuntu/ trusty/main libjasper1 amd64 1.900.1-14ubuntu3 [129 kB]
Holen: 8 http://de.archive.ubuntu.com/ubuntu/ trusty/main liblcms2-2 amd64 2.5-0ubuntu4 [132 kB]
Holen: 9 http://de.archive.ubuntu.com/ubuntu/ trusty/main liblqr-1-0 amd64 0.4.1-2ubuntu1 [23,4 kB]
Holen: 10 http://de.archive.ubuntu.com/ubuntu/ trusty/main libmagickcore5 amd64 8:6.7.7.10-6ubuntu3 [1.469 kB]
Holen: 11 http://de.archive.ubuntu.com/ubuntu/ trusty/main libmagickwand5 amd64 8:6.7.7.10-6ubuntu3 [266 kB]
Holen: 12 http://de.archive.ubuntu.com/ubuntu/ trusty/main libopts25 amd64 1:5.18-2ubuntu2 [55,3 kB]
Holen: 13 http://de.archive.ubuntu.com/ubuntu/ trusty/main libpaper1 amd64 1.1.24+nmu2ubuntu3 [13,4 kB]
Holen: 14 http://de.archive.ubuntu.com/ubuntu/ trusty/main ntp amd64 1:4.2.6.p5+dfsg-3ubuntu2 [611 kB]
Holen: 15 http://de.archive.ubuntu.com/ubuntu/ trusty/universe php-xml-parser all 1.3.4-6 [24,8 kB]
Holen: 16 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main php5-curl amd64 5.5.9+dfsg-1ubuntu4.4 [27,2 kB]
Holen: 17 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/universe php5-intl amd64 5.5.9+dfsg-1ubuntu4.4 [109 kB]
Holen: 18 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main php5-pgsql amd64 5.5.9+dfsg-1ubuntu4.4 [51,8 kB]
Holen: 19 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main php5-sqlite amd64 5.5.9+dfsg-1ubuntu4.4 [24,2 kB]
Holen: 20 http://de.archive.ubuntu.com/ubuntu/ trusty/main poppler-data all 0.4.6-4 [1.479 kB]
Holen: 21 http://de.archive.ubuntu.com/ubuntu/ trusty/main libijs-0.35 amd64 0.35-8build1 [16,8 kB]
Holen: 22 http://de.archive.ubuntu.com/ubuntu/ trusty/main libjbig2dec0 amd64 0.11+20120125-1ubuntu1 [48,6 kB]
Holen: 23 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libgs9-common all 9.10~dfsg-0ubuntu10.2 [2.068 kB]
Holen: 24 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libgs9 amd64 9.10~dfsg-0ubuntu10.2 [1.942 kB]
Holen: 25 http://de.archive.ubuntu.com/ubuntu/ trusty/main gsfonts all 1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1 [3.374 kB]
Holen: 26 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main ghostscript amd64 9.10~dfsg-0ubuntu10.2 [40,8 kB]
Holen: 27 http://de.archive.ubuntu.com/ubuntu/ trusty/main libpaper-utils amd64 1.1.24+nmu2ubuntu3 [8.244 B]
Holen: 28 http://de.archive.ubuntu.com/ubuntu/ trusty/universe php5-imagick amd64 3.1.2-1build1 [95,1 kB]
Es wurden 42,9 MB in 9 s geholt (4.397 kB/s).                                  
Vorkonfiguration der Pakete ...
Vormals nicht ausgewähltes Paket imagemagick-common wird gewählt.
(Lese Datenbank ... 130752 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../imagemagick-common_8%3a6.7.7.10-6ubuntu3_all.deb ...
Entpacken von imagemagick-common (8:6.7.7.10-6ubuntu3) ...
Vormals nicht ausgewähltes Paket libcupsfilters1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libcupsfilters1_1.0.52-0ubuntu1.2_amd64.deb ...
Entpacken von libcupsfilters1:amd64 (1.0.52-0ubuntu1.2) ...
Vormals nicht ausgewähltes Paket libcupsimage2:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libcupsimage2_1.7.2-0ubuntu1.2_amd64.deb ...
Entpacken von libcupsimage2:amd64 (1.7.2-0ubuntu1.2) ...
Vormals nicht ausgewähltes Paket libfftw3-double3:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libfftw3-double3_3.3.3-7ubuntu3_amd64.deb ...
Entpacken von libfftw3-double3:amd64 (3.3.3-7ubuntu3) ...
Vormals nicht ausgewähltes Paket libicu52:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libicu52_52.1-3_amd64.deb ...
Entpacken von libicu52:amd64 (52.1-3) ...
Vormals nicht ausgewähltes Paket libjasper1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libjasper1_1.900.1-14ubuntu3_amd64.deb ...
Entpacken von libjasper1:amd64 (1.900.1-14ubuntu3) ...
Vormals nicht ausgewähltes Paket liblcms2-2:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../liblcms2-2_2.5-0ubuntu4_amd64.deb ...
Entpacken von liblcms2-2:amd64 (2.5-0ubuntu4) ...
Vormals nicht ausgewähltes Paket liblqr-1-0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../liblqr-1-0_0.4.1-2ubuntu1_amd64.deb ...
Entpacken von liblqr-1-0:amd64 (0.4.1-2ubuntu1) ...
Vormals nicht ausgewähltes Paket libmagickcore5:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libmagickcore5_8%3a6.7.7.10-6ubuntu3_amd64.deb ...
Entpacken von libmagickcore5:amd64 (8:6.7.7.10-6ubuntu3) ...
Vormals nicht ausgewähltes Paket libmagickwand5:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libmagickwand5_8%3a6.7.7.10-6ubuntu3_amd64.deb ...
Entpacken von libmagickwand5:amd64 (8:6.7.7.10-6ubuntu3) ...
Vormals nicht ausgewähltes Paket libopts25:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libopts25_1%3a5.18-2ubuntu2_amd64.deb ...
Entpacken von libopts25:amd64 (1:5.18-2ubuntu2) ...
Vormals nicht ausgewähltes Paket libpaper1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libpaper1_1.1.24+nmu2ubuntu3_amd64.deb ...
Entpacken von libpaper1:amd64 (1.1.24+nmu2ubuntu3) ...
Vormals nicht ausgewähltes Paket ntp wird gewählt.
Vorbereitung zum Entpacken von .../ntp_1%3a4.2.6.p5+dfsg-3ubuntu2_amd64.deb ...
Entpacken von ntp (1:4.2.6.p5+dfsg-3ubuntu2) ...
Vormals nicht ausgewähltes Paket php-xml-parser wird gewählt.
Vorbereitung zum Entpacken von .../php-xml-parser_1.3.4-6_all.deb ...
Entpacken von php-xml-parser (1.3.4-6) ...
Vormals nicht ausgewähltes Paket php5-curl wird gewählt.
Vorbereitung zum Entpacken von .../php5-curl_5.5.9+dfsg-1ubuntu4.4_amd64.deb ...
Entpacken von php5-curl (5.5.9+dfsg-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket php5-intl wird gewählt.
Vorbereitung zum Entpacken von .../php5-intl_5.5.9+dfsg-1ubuntu4.4_amd64.deb ...
Entpacken von php5-intl (5.5.9+dfsg-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket php5-pgsql wird gewählt.
Vorbereitung zum Entpacken von .../php5-pgsql_5.5.9+dfsg-1ubuntu4.4_amd64.deb ...
Entpacken von php5-pgsql (5.5.9+dfsg-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket php5-sqlite wird gewählt.
Vorbereitung zum Entpacken von .../php5-sqlite_5.5.9+dfsg-1ubuntu4.4_amd64.deb ...
Entpacken von php5-sqlite (5.5.9+dfsg-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket poppler-data wird gewählt.
Vorbereitung zum Entpacken von .../poppler-data_0.4.6-4_all.deb ...
Entpacken von poppler-data (0.4.6-4) ...
Vormals nicht ausgewähltes Paket libijs-0.35 wird gewählt.
Vorbereitung zum Entpacken von .../libijs-0.35_0.35-8build1_amd64.deb ...
Entpacken von libijs-0.35 (0.35-8build1) ...
Vormals nicht ausgewähltes Paket libjbig2dec0 wird gewählt.
Vorbereitung zum Entpacken von .../libjbig2dec0_0.11+20120125-1ubuntu1_amd64.deb ...
Entpacken von libjbig2dec0 (0.11+20120125-1ubuntu1) ...
Vormals nicht ausgewähltes Paket libgs9-common wird gewählt.
Vorbereitung zum Entpacken von .../libgs9-common_9.10~dfsg-0ubuntu10.2_all.deb ...
Entpacken von libgs9-common (9.10~dfsg-0ubuntu10.2) ...
Vormals nicht ausgewähltes Paket libgs9 wird gewählt.
Vorbereitung zum Entpacken von .../libgs9_9.10~dfsg-0ubuntu10.2_amd64.deb ...
Entpacken von libgs9 (9.10~dfsg-0ubuntu10.2) ...
Vormals nicht ausgewähltes Paket gsfonts wird gewählt.
Vorbereitung zum Entpacken von .../gsfonts_1%3a8.11+urwcyr1.0.7~pre44-4.2ubuntu1_all.deb ...
Entpacken von gsfonts (1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1) ...
Vormals nicht ausgewähltes Paket ghostscript wird gewählt.
Vorbereitung zum Entpacken von .../ghostscript_9.10~dfsg-0ubuntu10.2_amd64.deb ...
Entpacken von ghostscript (9.10~dfsg-0ubuntu10.2) ...
Vormals nicht ausgewähltes Paket libpaper-utils wird gewählt.
Vorbereitung zum Entpacken von .../libpaper-utils_1.1.24+nmu2ubuntu3_amd64.deb ...
Entpacken von libpaper-utils (1.1.24+nmu2ubuntu3) ...
Vormals nicht ausgewähltes Paket owncloud wird gewählt.
Vorbereitung zum Entpacken von .../owncloud_7.0.2-1_all.deb ...
Entpacken von owncloud (7.0.2-1) ...
```

As you can see, unfortunately the screen output is in German. Nevertheless, as you can also see, it just hangs (for weeks, if I do nothing) at "Entpacken" (unpacking) the owncloud deb. Terminating with Ctrl-C is not possible, I have to kill the entire terminal, start a new one and kill -9 the hanging dpkg-deb tasks (3 of them).

Of I then run

```
dkpg --configure -a
```

dkpg installs most of the additional components - but not owncloud, of course:

```
root@[mymachine]:/home/[myhome]# dpkg --configure -a
libopts25:amd64 (1:5.18-2ubuntu2) wird eingerichtet ...
php5-pgsql (5.5.9+dfsg-1ubuntu4.4) wird eingerichtet ...

Creating config file /etc/php5/mods-available/pgsql.ini with new version
php5_invoke: Enable module pgsql for apache2 SAPI
php5_invoke: Enable module pgsql for cli SAPI

Creating config file /etc/php5/mods-available/pdo_pgsql.ini with new version
php5_invoke: Enable module pdo_pgsql for apache2 SAPI
php5_invoke: Enable module pdo_pgsql for cli SAPI
liblcms2-2:amd64 (2.5-0ubuntu4) wird eingerichtet ...
imagemagick-common (8:6.7.7.10-6ubuntu3) wird eingerichtet ...
libcupsfilters1:amd64 (1.0.52-0ubuntu1.2) wird eingerichtet ...
gsfonts (1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1) wird eingerichtet ...
php-xml-parser (1.3.4-6) wird eingerichtet ...
php5-sqlite (5.5.9+dfsg-1ubuntu4.4) wird eingerichtet ...

Creating config file /etc/php5/mods-available/sqlite3.ini with new version
php5_invoke: Enable module sqlite3 for apache2 SAPI
php5_invoke: Enable module sqlite3 for cli SAPI

Creating config file /etc/php5/mods-available/pdo_sqlite.ini with new version
php5_invoke: Enable module pdo_sqlite for apache2 SAPI
php5_invoke: Enable module pdo_sqlite for cli SAPI
poppler-data (0.4.6-4) wird eingerichtet ...
php5-curl (5.5.9+dfsg-1ubuntu4.4) wird eingerichtet ...

Creating config file /etc/php5/mods-available/curl.ini with new version
php5_invoke: Enable module curl for apache2 SAPI
php5_invoke: Enable module curl for cli SAPI
libicu52:amd64 (52.1-3) wird eingerichtet ...
ntp (1:4.2.6.p5+dfsg-3ubuntu2) wird eingerichtet ...
 * Starting NTP server ntpd                                              [ OK ] 
libgs9-common (9.10~dfsg-0ubuntu10.2) wird eingerichtet ...
update-alternatives: /usr/share/ghostscript/9.10 wird verwendet, um /usr/share/ghostscript/current (ghostscript-current) im Auto-Modus bereitzustellen
libijs-0.35 (0.35-8build1) wird eingerichtet ...
libjasper1:amd64 (1.900.1-14ubuntu3) wird eingerichtet ...
libfftw3-double3:amd64 (3.3.3-7ubuntu3) wird eingerichtet ...
libpaper1:amd64 (1.1.24+nmu2ubuntu3) wird eingerichtet ...

Creating config file /etc/papersize with new version
liblqr-1-0:amd64 (0.4.1-2ubuntu1) wird eingerichtet ...
libjbig2dec0 (0.11+20120125-1ubuntu1) wird eingerichtet ...
php5-intl (5.5.9+dfsg-1ubuntu4.4) wird eingerichtet ...

Creating config file /etc/php5/mods-available/intl.ini with new version
php5_invoke: Enable module intl for apache2 SAPI
php5_invoke: Enable module intl for cli SAPI
libcupsimage2:amd64 (1.7.2-0ubuntu1.2) wird eingerichtet ...
libmagickcore5:amd64 (8:6.7.7.10-6ubuntu3) wird eingerichtet ...
libmagickwand5:amd64 (8:6.7.7.10-6ubuntu3) wird eingerichtet ...
php5-imagick (3.1.2-1build1) wird eingerichtet ...
php5_invoke: Enable module imagick for apache2 SAPI
php5_invoke: Enable module imagick for cli SAPI
libgs9 (9.10~dfsg-0ubuntu10.2) wird eingerichtet ...
libpaper-utils (1.1.24+nmu2ubuntu3) wird eingerichtet ...
ghostscript (9.10~dfsg-0ubuntu10.2) wird eingerichtet ...
Trigger für libc-bin (2.19-0ubuntu6.3) werden verarbeitet ...
Trigger für libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.4) werden verarbeitet ...
Trigger für ureadahead (0.100.0-16) werden verarbeitet ...
```

Retrying to install owncloud skips the additional packages to be installed (of course), and still leads to apt-get (dpkg, actually) hanging at "unpacking".

Now, if I could get some kind of error or information on what precisely during unpacking is not progressing, I might be able to fix it. But, as said in the initial post, I don't know how to get more output from apt-get or dpkg.

Thanks for your help!

---

