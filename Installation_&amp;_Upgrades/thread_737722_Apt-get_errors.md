---
title: "Apt-get errors"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by gebj2 on 2008-03-27
Hi guys,

Ubuntu was going so very well for me for a few months and now I've gone and really screwed it up. Anyone willing to point me in the right direction. I'm really out of my depth. I can't add any more software at the moment.


gareth@gareth-laptop:~$ sudo apt-get install
[sudo] password for gareth:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.22-14-generic
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
5 not fully installed or removed.
Need to get 0B/18.8MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected
(Reading database ... 106726 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Exec format error
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Preparing to replace sox 13.0.0-1build1 (using .../sox_13.0.0-1build1_i386.deb) ...
Unpacking replacement sox ...
/bin/sh: Can't open update-mime
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/bin/sh: Can't open update-mime
dpkg: error processing /var/cache/apt/archives/sox_13.0.0-1build1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
/bin/sh: Can't open update-mime
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace vorbis-tools 1.1.1-13build1 (using .../vorbis-tools_1.1.1-13build1_i386.deb) ...
Unpacking replacement vorbis-tools ...
/bin/sh: Can't open update-mime
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/bin/sh: Can't open update-mime
dpkg: error processing /var/cache/apt/archives/vorbis-tools_1.1.1-13build1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
/bin/sh: Can't open update-mime
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
 /var/cache/apt/archives/sox_13.0.0-1build1_i386.deb
 /var/cache/apt/archives/vorbis-tools_1.1.1-13build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
gareth@gareth-laptop:~$

---

### Post by eivind on 2008-03-28
This may be a dumb question, but wouldn't the correct command here be

sudo apt-get dist-upgrade

?

---

### Post by gebj2 on 2008-03-28
That seems to do much the same - Arhhhhhh - what a mess

gareth@gareth-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  app-install-data-commercial evolution evolution-common evolution-plugins
  firefox firefox-gnome-support libcdio6 libicu36 libkrb53
  libnautilus-extension1 libpcre3 libpcrecpp0 libsdl-image1.2 libvlc0
  libvolume-id0 linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-image-2.6.22-14-generic linux-libc-dev mplayer nautilus nautilus-data
  tzdata udev unzip vlc vlc-nox vlc-plugin-esd volumeid
  xserver-xorg-video-intel
30 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/70.9MB of archives.
After unpacking 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected
(Reading database ... u106726 files and directories currently installed.)
iPreparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
tdpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Exec format error
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Preparing to replace sox 13.0.0-1build1 (using .../sox_13.0.0-1build1_i386.deb) ...
Unpacking replacement sox ...
/bin/sh: Can't open update-mime
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/bin/sh: Can't open update-mime
dpkg: error processing /var/cache/apt/archives/sox_13.0.0-1build1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
/bin/sh: Can't open update-mime
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace vorbis-tools 1.1.1-13build1 (using .../vorbis-tools_1.1.1-13build1_i386.deb) ...
Unpacking replacement vorbis-tools ...
/bin/sh: Can't open update-mime
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/bin/sh: Can't open update-mime
dpkg: error processing /var/cache/apt/archives/vorbis-tools_1.1.1-13build1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
/bin/sh: Can't open update-mime
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace tzdata 2007k-0ubuntu0.7.10 (using .../tzdata_2007k-0ubuntu0.7.10.1_all.deb) ...
Unpacking replacement tzdata ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
 /var/cache/apt/archives/sox_13.0.0-1build1_i386.deb
 /var/cache/apt/archives/vorbis-tools_1.1.1-13build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lswest on 2008-03-28
try this:
```
sudo apt-get install -f
sudo dpkg --configure -a
```

see if that helps.  The problem is the 5 packages not fully installed/upgraded.  Try rebooting and then re-running the commands too.

---

### Post by PmDematagoda on 2008-03-28
Clear the archive using:-
```
sudo apt-get clean
```

Then try running:-
```
sudo apt-get install -f
```

---

### Post by gebj2 on 2008-03-28
thanks for your help guys - I'm still getting the following I'm afraid


gareth@gareth-laptop:~$ sudo apt-get clean


gareth@gareth-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.22-14-generic
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
6 not fully installed or removed.
Need to get 18.8MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main linux-image-2.6.22-14-generic 2.6.22-14.52 [18.5MB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe sox 13.0.0-1build1 [199kB]   
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main vorbis-tools 1.1.1-13build1 [99.3kB]
Fetched 18.8MB in 21s (859kB/s)                                                
Reading changelogs... Done
/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected
(Reading database ... 106726 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Exec format error
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


gareth@gareth-laptop:~$ sudo dpkg --configure -a
Setting up tzdata (2007k-0ubuntu0.7.10.1) ...
/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up apt-listchanges (2.74ubuntu3.1) ...
/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing apt-listchanges (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ubuntu-docs (7.10.5) ...
/bin/sh: Can't open update-alternatives
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 tzdata
 linux-image-2.6.22-14-generic
 apt-listchanges
 ubuntu-docs

---

### Post by Zeral on 2008-04-02
Got the same problems here, doesn't matter what command i give, same final output.
Problems started when upgrading from 7.04 to 7.10 and - against better hope - stayed after upgrading to 8.04 HardyHeron.

Commands used:
apt-get -f install
apt-get upgrade
dpkg --configure -a
apt-get autoremove
etc etc

All say that they see that there are 3 not properly installed pkgs left and start up depmod wich will give allways the exact following result:
> Failed to run depmod
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help, cause it's not possible to update anymore and I really don't know what to do anymore.......

tia

---

### Post by Zeral on 2008-04-09
bump

---

