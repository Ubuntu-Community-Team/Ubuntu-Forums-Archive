---
title: "Ubuntu-Wont Upgrade or install"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by XxDeathXx on 2011-06-03
Ok--- Long story short. Bought the book "Hackiwng the art of exploitation" came with Ubuntu cd. to make it easier i installed it. Gave me no option to dual boot with windows so now i am #*$*%ed and deciding to try this out. Problem...
Go to Ubuntu website, cant install my upgrade.
I wanted to do this, because nothing else i try to install will.
I've looked all over the internet.
The codes below fail me.
sudo apt-get update
sudo apt-get upgrade


host security.ubuntu.com 
works for me in the terminal

I've read this in other forums, but it confuses/fails me as well

[I]"pt is portugal right? Could you try an alternative mirror?

eg gb.archive.ubuntu.com or nl.archive.ubuntu.com and see if that works?

Quick one-liner:

sudo perl -p -i.orig -e 's/pt.ar/nl.ar/g' /etc/apt/sources.list
This will create a backup (/etc/apt/sources.list.orig).

Then, aptitude update and see how that goes."[/I] 

if you couldnt tell i am ubuntu noob.
Help plz

---

### Post by Old_Grey_Wolf on 2011-06-03
We all live in different time zones; therefore, it make take several people to help solve this problem. We need to go step-by-step. 

I will start.

Open the terminal and type or copy/paste the command ```
sudo apt-get update
``` Copy and past the output of that command in a replying to this thread. Click on the # icon and paste the output between the [CODE[SIZE="1"] [/SIZE]][/CODE[SIZE="1"] [/SIZE]] tags.

Open the terminal and type or copy/paste the command ```
sudo apt-get upgrade
``` Copy and past the output of that command in a replying to this thread. Click on the # icon and paste the output between the [CODE[SIZE="1"] [/SIZE]][/CODE[SIZE="1"] [/SIZE]] tags.

Open the terminal and type or copy/paste the command ```
cat ../../etc/apt/sources.list
``` Copy and past the output of that command in a replying to this thread. Click on the # icon and paste the output between the [CODE[SIZE="1"] [/SIZE]][/CODE[SIZE="1"] [/SIZE]] tags.

---

### Post by XxDeathXx on 2011-06-03
Thank you very much for the quick reply. heres the first command--

```

Ign http://us.archive.ubuntu.com feisty Release.gpg
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates Release.gpg
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty-updates Release
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://security.ubuntu.com feisty-security/main Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/restricted Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/main Sources
  404 Not Found [IP: 91.189.92.166 80]
Ign http://us.archive.ubuntu.com feisty-updates/main Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Sources
Err http://us.archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/main Sources
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/restricted Sources
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/universe Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/universe Sources
  404 Not Found [IP: 91.189.92.161 80]
Err http://security.ubuntu.com feisty-security/restricted Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  404 Not Found [IP: 91.189.92.161 80]
Err http://security.ubuntu.com feisty-security/multiverse Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/multiverse Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://us.archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  404 Not Found [IP: 91.189.92.161 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.161 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

second command--
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host
  capplets-data dbus dbus-1-utils dnsutils evolution-data-server
  evolution-data-server-common file firefox firefox-gnome-support gimp
  gimp-data gimp-python gnome-app-install gnome-control-center gnome-panel
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables
  language-pack-ar language-pack-bn language-pack-de language-pack-en
  language-pack-es language-pack-fr language-pack-gnome-ar
  language-pack-gnome-bn language-pack-gnome-de language-pack-gnome-en
  language-pack-gnome-es language-pack-gnome-fr language-pack-gnome-hi
  language-pack-gnome-pt language-pack-gnome-ru language-pack-gnome-xh
  language-pack-pt language-pack-ru libbind9-0 libcamel1.2-10 libcurl3
  libdbus-1-3 libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libexif12 libfreetype6
  libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa
  libgnome-window-settings1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1
  libkrb53 liblwres9 libmagic1 libmagick9 libmetacity0 libnspr4 libnss3
  libpanel-applet2-0 libpng12-0 libpoppler1 libpoppler1-glib libslab0
  libsmbclient libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 linux-generic
  linux-libc-dev linux-restricted-modules-common mesa-utils metacity
  metacity-common openssl poppler-utils python python-apport python-gdbm
  python-launchpad-bugs python-minimal python-problem-report python2.5
  python2.5-minimal rdesktop rsync samba-common smbclient tar tcpdump
  ttf-opensymbol tzdata unattended-upgrades update-manager update-manager-core
  xscreensaver-data xscreensaver-gl
112 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 75.1MB of archives.
After unpacking 31.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tar python2.5 python2.5-minimal python python-minimal language-pack-ar
  language-pack-bn language-pack-de language-pack-en language-pack-es
  language-pack-fr language-pack-gnome-ar language-pack-gnome-bn
  language-pack-gnome-de language-pack-gnome-en language-pack-gnome-es
  language-pack-gnome-fr language-pack-gnome-hi language-pack-gnome-pt
  language-pack-gnome-ru language-pack-gnome-xh language-pack-pt
  language-pack-ru tzdata libdbus-1-3 libisc11 libdns22 libisccc0 libisccfg1
  libbind9-0 liblwres9 bind9-host dnsutils file libmagic1 iptables libkrb53
  rsync tcpdump update-manager-core app-install-data
  app-install-data-commercial python-problem-report python-launchpad-bugs
  python-apport apport apport-gtk capplets-data dbus dbus-1-utils
  libedataserver1.2-9 libnspr4 libnss3 libcamel1.2-10 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13
  evolution-data-server evolution-data-server-common firefox-gnome-support
  libfreetype6 firefox gimp gimp-data libexif12 libgimp2.0 libpng12-0
  gimp-python python-gdbm gnome-app-install metacity-common libmetacity0
  libpanel-applet2-0 libslab0 gnome-control-center libgnome-window-settings1
  libedataserverui1.2-8 gnome-panel gnome-panel-data hwdb-client-common
  hwdb-client-gnome libcurl3 libexchange-storage1.2-3 libgl1-mesa-dri
  libgl1-mesa-glx libjasper-1.701-1 libmagick9 libpoppler1-glib libpoppler1
  libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 linux-generic
  linux-libc-dev linux-restricted-modules-common metacity openssl
  poppler-utils rdesktop smbclient samba-common ttf-opensymbol
  unattended-upgrades update-manager xscreensaver-data libglu1-mesa
  xscreensaver-gl libsmbclient mesa-utils
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com feisty-updates/main python2.5 2.5.1-0ubuntu1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main python2.5-minimal 2.5.1-0ubuntu1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main python 2.5.1-0ubuntu3
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main tar 1.16-2ubuntu0.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libisc11 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libdns22 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main python-minimal 2.5.1-0ubuntu3
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-ar 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-bn 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-de 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-en 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-es 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-fr 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libisccc0 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libisccfg1 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libbind9-0 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main liblwres9 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main bind9-host 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main dnsutils 1:9.3.4-2ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main file 4.19-1ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-ar 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-bn 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-de 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libmagic1 4.19-1ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libkrb53 1.4.4-5ubuntu3.3
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main rsync 2.6.9-3ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-en 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-es 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-fr 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-hi 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-pt 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-ru 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-gnome-xh 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main tcpdump 3.9.5-2ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libedataserver1.2-9 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libnspr4 2:1.firefox2.0.0.6+1-0ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libnss3 2:1.firefox2.0.0.6+1-0ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libcamel1.2-10 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libebook1.2-9 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libecal1.2-7 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-pt 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main language-pack-ru 1:7.04+20070601
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main tzdata 2007f-0ubuntu0.7.4
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libdbus-1-3 1.0.2-1ubuntu4
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main iptables 1.3.6.0debian1-5ubuntu2.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main update-manager-core 1:0.59.25
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main app-install-data 0.3.31
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main app-install-data-commercial 7.3
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libedata-book1.2-2 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libedata-cal1.2-6 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libegroupwise1.2-13 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main python-problem-report 0.76.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main python-launchpad-bugs 0.1.13.2
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main python-apport 0.76.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main apport 0.76.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main apport-gtk 0.76.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main capplets-data 1:2.18.1-0ubuntu2.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main dbus 1.0.2-1ubuntu4
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main dbus-1-utils 1.0.2-1ubuntu4
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main python-gdbm 2.5.1-0ubuntu1
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main evolution-data-server 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main evolution-data-server-common 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main firefox-gnome-support 2.0.0.6+1-0ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libfreetype6 2.2.1-5ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main firefox 2.0.0.6+1-0ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main gimp 2.2.13-1ubuntu4.3
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main gimp-data 2.2.13-1ubuntu4.3
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main gnome-app-install 0.3.31
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main metacity-common 1:2.18.2-0ubuntu1.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libmetacity0 1:2.18.2-0ubuntu1.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libpanel-applet2-0 1:2.18.1-0ubuntu3.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libslab0 1:2.18.1-0ubuntu2.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main gnome-control-center 1:2.18.1-0ubuntu2.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libgnome-window-settings1 1:2.18.1-0ubuntu2.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main gnome-panel 1:2.18.1-0ubuntu3.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libexif12 0.6.13-5ubuntu0.2
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libgimp2.0 2.2.13-1ubuntu4.3
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libpng12-0 1.2.15~beta5-1ubuntu1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main gnome-panel-data 1:2.18.1-0ubuntu3.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main hwdb-client-common 0.6.10.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main hwdb-client-gnome 0.6.10.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libgl1-mesa-dri 6.5.2-3ubuntu8
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main libgl1-mesa-glx 6.5.2-3ubuntu8
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main metacity 1:2.18.2-0ubuntu1.1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main rdesktop 1.5.0-1ubuntu1
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main unattended-upgrades 0.23ubuntu3
  404 Not Found [IP: 91.189.92.162 80]
Err http://us.archive.ubuntu.com feisty-updates/main update-manager 1:0.59.25
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main gimp-python 2.2.13-1ubuntu4.3
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libedataserverui1.2-8 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libcurl3 7.15.5-1ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libexchange-storage1.2-3 1.10.1-0ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libjasper-1.701-1 1.701.0-2ubuntu0.7.04
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libmagick9 7:6.2.4.5.dfsg1-0.14ubuntu0.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libpoppler1-glib 0.5.4-0ubuntu8.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main libglu1-mesa 6.5.2-3ubuntu8
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libpoppler1 0.5.4-0ubuntu8.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libvorbis0a 1.1.2.dfsg-1.2ubuntu2
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libvorbisenc2 1.1.2.dfsg-1.2ubuntu2
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com feisty-updates/main mesa-utils 6.5.2-3ubuntu8
  404 Not Found [IP: 91.189.92.162 80]
Err http://security.ubuntu.com feisty-security/main libvorbisfile3 1.1.2.dfsg-1.2ubuntu2
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libwrap0 7.6.dbs-11ubuntu0.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/restricted linux-generic 2.6.20.16.28.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-16.32
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/restricted linux-restricted-modules-common 2.6.20.5-16.29
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main openssl 0.9.8c-4ubuntu0.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main poppler-utils 0.5.4-0ubuntu8.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main smbclient 3.0.24-2ubuntu1.2
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main samba-common 3.0.24-2ubuntu1.2
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main ttf-opensymbol 2.2.0-1ubuntu4
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main xscreensaver-data 4.24-5ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main xscreensaver-gl 4.24-5ubuntu2.1
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com feisty-security/main libsmbclient 3.0.24-2ubuntu1.2
  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.5.1-0ubuntu3_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-minimal_2.5.1-0ubuntu3_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-bn/language-pack-bn_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-de/language-pack-de_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-es/language-pack-es_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-fr/language-pack-fr_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ar/language-pack-gnome-ar_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-bn/language-pack-gnome-bn_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-de/language-pack-gnome-de_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-es/language-pack-gnome-es_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-fr/language-pack-gnome-fr_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-hi/language-pack-gnome-hi_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-pt/language-pack-gnome-pt_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ru/language-pack-gnome-ru_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-xh/language-pack-gnome-xh_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-pt/language-pack-pt_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ru/language-pack-ru_7.04+20070601_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007f-0ubuntu0.7.4_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu4_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns22_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc0_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg1_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-0_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres9_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.3.4-2ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/file/file_4.19-1ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.19-1ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.6.0debian1-5ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.4.4-5ubuntu3.3_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-3ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.9.5-2ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.25_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.3.31_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_7.3_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_0.76.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bughelper/python-launchpad-bugs_0.1.13.2_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_0.76.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_0.76.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_0.76.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.18.1-0ubuntu2.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.0.2-1ubuntu4_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_1.0.2-1ubuntu4_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-9_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.6+1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.6+1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-10_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.10.1-0ubuntu1.1_all.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.6+1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.2.1-5ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.6+1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.13-1ubuntu4.3_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.13-1ubuntu4.3_all.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.13-5ubuntu0.2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.13-1ubuntu4.3_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-python_2.2.13-1ubuntu4.3_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-gdbm_2.5.1-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.3.31_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity-common_2.18.2-0ubuntu1.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.18.2-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.18.1-0ubuntu3.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/libslab0_2.18.1-0ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.18.1-0ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/libgnome-window-settings1_2.18.1-0ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.18.1-0ubuntu3.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.18.1-0ubuntu3.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-common_0.6.10.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-gnome_0.6.10.1_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.15.5-1ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_1.10.1-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.5.2-3ubuntu8_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_6.5.2-3ubuntu8_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.7.04_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5.dfsg1-0.14ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1-glib_0.5.4-0ubuntu8.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1_0.5.4-0ubuntu8.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.1.2.dfsg-1.2ubuntu2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.1.2.dfsg-1.2ubuntu2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.1.2.dfsg-1.2ubuntu2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tcp-wrappers/libwrap0_7.6.dbs-11ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.20.16.28.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.32_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-common_2.6.20.5-16.29_all.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.18.2-0ubuntu1.1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.5.4-0ubuntu8.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-1ubuntu1_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.2.0-1ubuntu4_all.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unattended-upgrades/unattended-upgrades_0.23ubuntu3_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.25_all.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-data_4.24-5ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_6.5.2-3ubuntu8_i386.deb  404 Not Found [IP: 91.189.92.162 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver-gl_4.24-5ubuntu2.1_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.2_i386.deb  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_6.5.2-3ubuntu8_i386.deb  404 Not Found [IP: 91.189.92.162 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Third Command--
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```


Thank you for the help. I am very grateful.

---

### Post by Old_Grey_Wolf on 2011-06-03
The output from the commands show the disk you got was for Ubuntu 7.04 (Feisty Fawn). That release of Ubuntu has not been supported since [correction, October 2008] April 2010. The book and disk are outdated. You can't get updates for unsupported releases.

You will need to download a newer release of Ubuntu, make a boot-able CD or USB, and install it. I would go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and select the 10.04 LTS release for download. The 10.04 LTS release is supported until April 2013.

Most of what is in the book should still apply to the 10.04 LTS Ubuntu release.

---

### Post by Bucky Ball on 2011-06-03
As the Wolf says ...

You will get a much smoother ride with 10.04 LTS. ;)

---

### Post by dFlyer on 2011-06-03
> **XxDeathXx said:**
> Ok--- Long story short. Bought the book "Hackiwng the art of exploitation" came with Ubuntu cd. to make it easier i installed it. Gave me no option to dual boot with windows so now i am #*$*%ed and deciding to try this out. Problem...
Go to Ubuntu website, cant install my upgrade.
I wanted to do this, because nothing else i try to install will.
I've looked all over the internet.
The codes below fail me.
sudo apt-get update
sudo apt-get upgrade


host security.ubuntu.com 
works for me in the terminal

I've read this in other forums, but it confuses/fails me as well

[I]"pt is portugal right? Could you try an alternative mirror?

eg gb.archive.ubuntu.com or nl.archive.ubuntu.com and see if that works?

Quick one-liner:

sudo perl -p -i.orig -e 's/pt.ar/nl.ar/g' /etc/apt/sources.list
This will create a backup (/etc/apt/sources.list.orig).

Then, aptitude update and see how that goes."[/I] 

if you couldnt tell i am ubuntu noob.
Help plz

What version of ubuntu did you install. The current verions is 11.04. The current LTS (long Term Support) is 10.04.

---

### Post by dFlyer on 2011-06-03
Sorry to double post, should have read further down. As stated 7.04 is no longer supported. I would recommend 10.04 LTS if your new to linux.

---

### Post by XxDeathXx on 2011-06-04
Thanks much Wolf. Thats depressing its that old but i'll get it working. thanks to the rest of you who woulda helped as well.

Problem is, im unsure how to make the startup disk, 
as shown in Ubuntu, 
it says to go to

System
Administration
Startup Disk creator

Alas, there is no Startup Disk Creater in my old version...
I hate being at a stand still.
recommendations?

---

### Post by thunder63cs on 2011-06-08
you can dl an img burner to take the img from the file you dl and put it where you want cd or usb the one I personally use is imgburn and have not had an issue with it yet.

---

