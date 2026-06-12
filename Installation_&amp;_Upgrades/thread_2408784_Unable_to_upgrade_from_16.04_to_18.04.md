---
title: "Unable to upgrade from 16.04 to 18.04"
date: 2018-12-23
forum: Installation &amp; Upgrades
---

### Post by smistry000 on 2018-12-23
When I do do-release-upgrade it says :


```

Could not determine the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Rea

```

Output of grep Broken /var/log/dist-upgrade/apt.log 


```

Broken libdouble-conversion1:amd64 Breaks on libdouble-conversion1v5 [ amd64 ] < 2.0.1-3ubuntu2 > ( libs )
Broken libsane1:amd64 Conflicts on libsane [ amd64 ] < 1.0.25+git20150528-1ubuntu2.16.04.1 > ( libs ) (< 1.0.27-1~)
Broken libsane1:amd64 Conflicts on libsane [ i386 ] < 1.0.25+git20150528-1ubuntu2.16.04.1 > ( libs ) (< 1.0.27-1~)
Broken libplexus-component-annotations-java:amd64 Breaks on libplexus-containers-java [ amd64 ] < 1.0~beta3.0.7-8 > ( java )
Broken imagemagick-6-common:amd64 Breaks on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.13 > ( libs ) (< 8:6.9.6.2+dfsg-3~)
Broken libcurl3:amd64 Conflicts on libcurl4 [ amd64 ] < none -> 7.58.0-2ubuntu3.5 > ( libs )
Broken hunspell-en-us:amd64 Conflicts on myspell-en-us [ amd64 ] < 1:5.1.0-1ubuntu2.2 > ( oldlibs )
Broken aptdaemon:amd64 Breaks on python3-aptdaemon.pkcompat [ amd64 ] < 1.1.1+bzr982-0ubuntu14 > ( python )
Broken curl:amd64 Depends on libcurl4 [ amd64 ] < none -> 7.58.0-2ubuntu3.5 > ( libs ) (= 7.58.0-2ubuntu3.5)
Broken vlc-bin:amd64 Breaks on vlc-nox [ amd64 ] < 2.2.2+git20170721+r59033+56~ubuntu16.04.1 > ( video ) (< 3.0.0-1~)
Broken xubuntu-default-settings:amd64 Breaks on upstart [ amd64 ] < 1.13.2-0ubuntu21.1 > ( admin ) (< 1.13.2-0ubuntu28~)
Broken fwupd:amd64 Breaks on libdfu1 [ amd64 ] < 0.8.3-0ubuntu4 > ( admin ) (< 0.9.7-1)
Broken libwebkitgtk-1.0-0:amd64 Breaks on libwebkitgtk-1.0-common [ amd64 ] < 2.4.11-0ubuntu0.1 > ( libs ) (< 2.4.11-2~)
Broken kerneloops:amd64 Breaks on kerneloops-daemon [ amd64 ] < 0.12+git20140509-2ubuntu1 > ( utils ) (< 0.12+git20140509-6ubuntu1)
Broken libwebkitgtk-3.0-0:amd64 Breaks on libwebkitgtk-3.0-common [ amd64 ] < 2.4.11-0ubuntu0.1 > ( libs ) (< 2.4.11-2~)
Broken python3-zope.interface:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.7-1~18.04 > ( python ) (< 3.6)
Broken libsasl2-modules:i386 Depends on libssl1.1 [ i386 ] < none -> 1.1.0g-2ubuntu4.3 > ( libs ) (>= 1.1.0)
Broken gstreamer1.0-plugins-ugly:amd64 Conflicts on gstreamer1.0-plugins-ugly-amr [ amd64 ] < 1.8.3-1ubuntu0.1 > ( libs ) (< 1.11.91)
Broken libgnutls28-dev:amd64 Conflicts on gnutls-dev [ amd64 ] < none ->  > ( none )
Broken gstreamer1.0-plugins-bad:amd64 Conflicts on gstreamer1.0-plugins-bad-faad [ amd64 ] < 1.8.3-1ubuntu0.2 > ( libs ) (< 1.11.91-1ubuntu1)
Broken gstreamer1.0-plugins-bad:amd64 Conflicts on gstreamer1.0-plugins-bad-videoparsers [ amd64 ] < 1.8.3-1ubuntu0.2 > ( libs ) (< 1.11.91-1ubuntu1)
Broken libglib2.0-dev:amd64 Depends on libpcre3-dev [ amd64 ] < none -> 2:8.39-9 > ( libdevel ) (>= 1:8.31)
Broken libcurl4-openssl-dev:amd64 Depends on libcurl4 [ amd64 ] < none -> 7.58.0-2ubuntu3.5 > ( libs ) (= 7.58.0-2ubuntu3.5)
Broken libabw-0.1-1:amd64 Conflicts on libabw-0.1-1v5 [ amd64 ] < 0.1.1-2ubuntu2 > ( libs )
Broken python3-certbot:amd64 Depends on python3-zope.interface [ amd64 ] < 4.3.2-1+ubuntu16.04.1+certbot+1 > ( zope )
Broken python3-xapian:amd64 Conflicts on python3-xapian1.3 [ amd64 ] < 1.3.4-0ubuntu1 > ( python )
Broken certbot:amd64 Depends on python3-certbot [ amd64 ] < 0.28.0-1+ubuntu16.04.1+certbot+4 > ( python ) (= 0.28.0-1+ubuntu16.04.1+certbot+4)
Broken libgjs0g:amd64 Conflicts on libgjs0e [ amd64 ] < 1.44.0-1ubuntu1 > ( libs )
Broken python3-zope.component:amd64 Depends on python3-zope.interface [ amd64 ] < 4.3.2-1+ubuntu16.04.1+certbot+1 > ( zope ) (>= 4.1.0)
Broken libharfbuzz-dev:amd64 Depends on libglib2.0-dev [ amd64 ] < none -> 2.56.3-0ubuntu0.18.04.1 > ( libdevel ) (>= 2.19.1)
Broken python3-lazr.restfulclient:amd64 Depends on python3-zope.interface [ amd64 ] < 4.3.2-1+ubuntu16.04.1+certbot+1 > ( zope )
Broken evince-gtk:amd64 Depends on evince [ amd64 ] < 3.18.2-1ubuntu4.3 -> 3.28.4-0ubuntu1 > ( gnome ) (= 3.18.2-1ubuntu4.3)
Broken python3-psycopg2:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.7-1~18.04 > ( python ) (< 3.6)
Broken libsidplay2:amd64 Conflicts on libsidplay2v5 [ amd64 ] < 2.1.1-14ubuntu2 > ( libs )
Broken perl-modules-5.22:amd64 Conflicts on perl-modules [ amd64 ] < none ->  > ( none )
Broken pgadmin4-common:amd64 Depends on python3-psycopg2 [ amd64 ] < 2.7.5-2.pgdg16.04+1 > ( python ) (>= 2.7.4)
Broken libvlccore8:amd64 Depends on vlc-data [ amd64 ] < 2.2.2+git20170721+r59033+56~ubuntu16.04.1 -> 3.0.4-1ubuntu0.2 > ( universe/graphics ) (= 2.2.2+git20170721+r59033+56~ubuntu16.04.1)
Broken libgtk2-appindicator-perl:amd64 Depends on perlapi-5.22.1 [ amd64 ] < none ->  > ( none )
Broken libgoo-canvas-perl:amd64 Depends on perlapi-5.22.1 [ amd64 ] < none ->  > ( none )
Broken python3-certbot-apache:amd64 Depends on certbot [ amd64 ] < 0.28.0-1+ubuntu16.04.1+certbot+4 > ( web ) (>= 0.26.0~)
Broken libmagickwand-6.q16-2:amd64 Depends on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.13 > ( libs ) (>= 8:6.8.9.9)
Broken python3-zope.hookable:amd64 Depends on python3 [ amd64 ] < 3.5.1-3 -> 3.6.7-1~18.04 > ( python ) (< 3.6)
Broken libunwind8-dev:amd64 Depends on libunwind-dev [ amd64 ] < 1.1-4.1 -> 1.2.1-8 > ( libdevel ) (= 1.1-4.1)
Broken libmagickcore-6.q16-2-extra:amd64 Depends on libmagickcore-6.q16-2 [ amd64 ] < 8:6.8.9.9-7ubuntu5.13 > ( libs ) (>= 8:6.8.9.9)
Broken xserver-xorg-video-mga:amd64 Depends on xorg-video-abi-20 [ amd64 ] < none ->  > ( none )
Broken libnss3-nssdb:amd64 Depends on libnss3 [ amd64 ] < 2:3.28.4-0ubuntu0.16.04.3 -> 2:3.35-2ubuntu2 > ( libs ) (= 2:3.28.4-0ubuntu0.16.04.3)
Broken upstart-bin:amd64 Depends on upstart [ amd64 ] < 1.13.2-0ubuntu21.1 > ( admin )
Broken xserver-xorg-video-cirrus:amd64 Depends on xorg-video-abi-20 [ amd64 ] < none ->  > ( none )
Broken xserver-xorg-input-vmmouse:amd64 Depends on xorg-input-abi-22 [ amd64 ] < none ->  > ( none )
Broken cups-pdf:amd64 Depends on printer-driver-cups-pdf [ amd64 ] < 2.6.1-21 -> 3.0.1-5 > ( universe/graphics ) (= 2.6.1-21)
Broken pulseaudio-module-x11:amd64 Depends on libpulse0 [ amd64 ] < 1:8.0-0ubuntu3.10 -> 1:11.1-1ubuntu7.1 > ( libs ) (= 1:8.0-0ubuntu3.10)
Broken pgadmin4:amd64 Depends on pgadmin4-common [ amd64 ] < 3.5-1.pgdg16.04+1 > ( database ) (= 3.5-1.pgdg16.04+1)
Broken python-certbot-apache:amd64 Depends on python3-certbot-apache [ amd64 ] < 0.28.0-1+ubuntu16.04.1+certbot+3 > ( python )
Broken libperl5.22:amd64 Depends on perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.6 > ( perl ) (>= 5.22.1-9ubuntu0.6)
Broken python3-launchpadlib:amd64 Depends on python3-lazr.restfulclient [ amd64 ] < none -> 0.13.5-1 > ( python ) (>= 0.11.2)
Broken libicu-le-hb-dev:amd64 Depends on libharfbuzz-dev [ amd64 ] < none -> 1.7.2-1ubuntu1 > ( libdevel )
Broken perl-modules-5.22:amd64 Conflicts on perl-modules [ amd64 ] < none ->  > ( none )
Broken libperl5.22:amd64 Depends on perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.6 > ( perl ) (>= 5.22.1-9ubuntu0.6)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken perl-modules-5.22:amd64 Conflicts on perl-modules [ amd64 ] < none ->  > ( none )
Broken libperl5.22:amd64 Depends on perl-modules-5.22 [ amd64 ] < 5.22.1-9ubuntu0.6 > ( perl ) (>= 5.22.1-9ubuntu0.6)
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )
Broken icu-devtools:amd64 Breaks on libicu-dev [ amd64 ] < 55.1-7ubuntu0.4 -> 60.2-3ubuntu3 > ( libdevel ) (< 60.2-3ubuntu3)
Broken libicu-dev:amd64 Depends on libicu-le-hb-dev [ amd64 ] < none -> 1.0.3+git161113-4 > ( libdevel )




```

Content of /etc/apt/sources.list


```

# deb cdrom:[Xubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422.1)]/ vivid main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner
# deb http://repos.zend.com/zend-server/early-access/php7/repos ubuntu/ # disabled on upgrade to xenial
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


```

---

### Post by Impavidus on 2018-12-23
You can remove the vivid partner repository from your sources.list. It's old. But I don't think that's the cause of your problem.

When you run```
sudo apt update
sudo apt upgrade
```do you get any error messages? If so, you must first fix those errors and complete the ordinary upgrade before you can run a release upgrade. But it'll be faster to do a clean install.

---

### Post by smistry000 on 2018-12-23
If have removed PPAs and the vivid partner repo then ran update + upgrade

```

Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]  
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]     
Fetched 323 kB in 0s (554 kB/s)                                                
Reading package lists... Done
sanish@spectre-xubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.



```

The do-release-upgrade is still failing though

---

