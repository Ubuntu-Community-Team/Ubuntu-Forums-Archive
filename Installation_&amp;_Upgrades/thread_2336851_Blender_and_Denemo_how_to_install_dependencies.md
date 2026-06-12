---
title: "Blender and Denemo: how to install dependencies?"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by hd.scania on 2016-09-12
```
root@HD-SCANIA:/home/hd_scania# apt install blender denemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not going to be installed
 aspell : Depends: dictionaries-common (> 0.40) but it is not going to be installed
 aspell-en : Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
 blender : Depends: blender-data (= 2.76.b+dfsg0-3build1) but it is not going to be installed
           Depends: fonts-dejavu but it is not going to be installed
           Depends: libavdevice-ffmpeg56 (>= 7:2.4) but it is not going to be installed
           Depends: libboost-locale1.58.0 but it is not going to be installed
           Depends: libboost-thread1.58.0 but it is not going to be installed
           Depends: libglew1.13 (>= 1.12.0) but it is not going to be installed
           Depends: libglu1-mesa but it is not going to be installed or
                    libglu1
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not going to be installed or
                    libjack-0.116
           Depends: libjemalloc1 (>= 2.1.1) but it is not going to be installed
           Depends: libopenal1 (>= 1.14) but it is not going to be installed
           Depends: libopencolorio1v5 but it is not going to be installed
           Depends: libopenimageio1.6 but it is not going to be installed
           Depends: libpython3.5 (>= 3.5.0~b1) but it is not going to be installed
           Depends: libspnav0 (>= 0.2.2) but it is not going to be installed
 denemo : Depends: guile-2.0-libs but it is not going to be installed
          Depends: libaubio4 but it is not going to be installed
          Depends: libevdocument3-4 (>= 3.0.2) but it is not going to be installed
          Depends: libevview3-3 (>= 3.0.2) but it is not going to be installed
          Depends: libfluidsynth1 but it is not going to be installed
          Depends: libgtksourceview-3.0-1 (>= 2.91.4) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113) but it is not going to be installed
          Depends: libportmidi0 but it is not going to be installed
          Depends: librubberband2v5 but it is not going to be installed
          Depends: libsmf0 (>= 1.3) but it is not going to be installed
          Depends: denemo-data (= 2.0.2-1) but it is not going to be installed
          Depends: ttf-denemo (= 2.0.2-1) but it is not going to be installed
          Recommends: denemo-doc (= 2.0.2-1) but it is not going to be installed
          Recommends: lilypond but it is not going to be installed
          Recommends: alsa
 hunspell-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@HD-SCANIA:/home/hd_scania# apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  dictionaries-common libgtk-3-bin
Suggested packages:
  wordlist
The following NEW packages will be installed:
  dictionaries-common libgtk-3-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
410 not fully installed or removed.
Need to get 239 kB of archives.
After this operation, 1,068 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk-3-bin amd64 3.18.9-1ubuntu3.1 [53.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 dictionaries-common all 1.26.3 [185 kB]
Fetched 239 kB in 2s (85.2 kB/s)             
Preconfiguring packages ...
root@HD-SCANIA:/home/hd_scania# apt purge dictionaries-common libgtk-3-bin && apt install --reinstall dictionaries-common libgtk-3-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'dictionaries-common' is not installed, so not removed
Package 'libgtk-3-bin' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not going to be installed
 aspell : Depends: dictionaries-common (> 0.40) but it is not going to be installed
 aspell-en : Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
 hunspell-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@HD-SCANIA:/home/hd_scania#
```
```
root@HD-SCANIA:/home/hd_scania# dpkg --configure -a && apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  dictionaries-common libgtk-3-bin
Suggested packages:
  wordlist
The following NEW packages will be installed:
  dictionaries-common libgtk-3-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
410 not fully installed or removed.
Need to get 239 kB of archives.
After this operation, 1,068 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk-3-bin amd64 3.18.9-1ubuntu3.1 [53.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 dictionaries-common all 1.26.3 [185 kB]
Fetched 239 kB in 2s (105 kB/s)              
Preconfiguring packages ...
root@HD-SCANIA:/home/hd_scania# apt install blender denemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not going to be installed
 aspell : Depends: dictionaries-common (> 0.40) but it is not going to be installed
 aspell-en : Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
 blender : Depends: blender-data (= 2.76.b+dfsg0-3build1) but it is not going to be installed
           Depends: fonts-dejavu but it is not going to be installed
           Depends: libavdevice-ffmpeg56 (>= 7:2.4) but it is not going to be installed
           Depends: libboost-locale1.58.0 but it is not going to be installed
           Depends: libboost-thread1.58.0 but it is not going to be installed
           Depends: libglew1.13 (>= 1.12.0) but it is not going to be installed
           Depends: libglu1-mesa but it is not going to be installed or
                    libglu1
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not going to be installed or
                    libjack-0.116
           Depends: libjemalloc1 (>= 2.1.1) but it is not going to be installed
           Depends: libopenal1 (>= 1.14) but it is not going to be installed
           Depends: libopencolorio1v5 but it is not going to be installed
           Depends: libopenimageio1.6 but it is not going to be installed
           Depends: libpython3.5 (>= 3.5.0~b1) but it is not going to be installed
           Depends: libspnav0 (>= 0.2.2) but it is not going to be installed
 denemo : Depends: guile-2.0-libs but it is not going to be installed
          Depends: libaubio4 but it is not going to be installed
          Depends: libevdocument3-4 (>= 3.0.2) but it is not going to be installed
          Depends: libevview3-3 (>= 3.0.2) but it is not going to be installed
          Depends: libfluidsynth1 but it is not going to be installed
          Depends: libgtksourceview-3.0-1 (>= 2.91.4) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113) but it is not going to be installed
          Depends: libportmidi0 but it is not going to be installed
          Depends: librubberband2v5 but it is not going to be installed
          Depends: libsmf0 (>= 1.3) but it is not going to be installed
          Depends: denemo-data (= 2.0.2-1) but it is not going to be installed
          Depends: ttf-denemo (= 2.0.2-1) but it is not going to be installed
          Recommends: denemo-doc (= 2.0.2-1) but it is not going to be installed
          Recommends: lilypond but it is not going to be installed
          Recommends: alsa
 hunspell-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@HD-SCANIA:/home/hd_scania#
```
```
root@HD-SCANIA:/home/hd_scania# apt clean && apt -f install && apt update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  dictionaries-common libgtk-3-bin
Suggested packages:
  wordlist
The following NEW packages will be installed:
  dictionaries-common libgtk-3-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
410 not fully installed or removed.
Need to get 239 kB of archives.
After this operation, 1,068 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk-3-bin amd64 3.18.9-1ubuntu3.1 [53.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 dictionaries-common all 1.26.3 [185 kB]
Fetched 239 kB in 2s (88.2 kB/s)             
Preconfiguring packages ...
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease             
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease          
Hit:3 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease     
Hit:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Get:6 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Fetched 247 kB in 3s (76.5 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@HD-SCANIA:/home/hd_scania# apt remove software-center && apt install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'software-center' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adwaita-icon-theme : Depends: libgtk-3-bin but it is not going to be installed
 aspell : Depends: dictionaries-common (> 0.40) but it is not going to be installed
 aspell-en : Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
 hunspell-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@HD-SCANIA:/home/hd_scania#
```
```
root@HD-SCANIA# apt remove gimp inkscape vlc winehq-devel
root@HD-SCANIA# ls /var/lib/apt/lists
archives.ubuntu.com.Xenial.Xerus.resources.00.deb
archives.ubuntu.com.Xenial.Xerus.resources.01.deb
archives.ubuntu.com.Xenial.Xerus.resources.02.deb
...
archives.ubuntu.com.Xenial.Xerus.resources.ff.deb
archives.ubuntu.com.Xenial.Xerus.security.00.deb
archives.ubuntu.com.Xenial.Xerus.security.01.deb
archives.ubuntu.com.Xenial.Xerus.security.02.deb
...
archives.ubuntu.com.Xenial.Xerus.security.ff.deb
archives.ubuntu.com.Xenial.Xerus.updates.00.deb
archives.ubuntu.com.Xenial.Xerus.updates.01.deb
archives.ubuntu.com.Xenial.Xerus.updates.02.deb
...
archives.ubuntu.com.Xenial.Xerus.updates.ff.deb
status
root@HD-SCANIA# cd /var/lib/apt/lists
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.4b.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.4b.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.4b.deb
root@HD-SCANIA/var/lib/apt/lists# cd /media/hd_scania
root@HD-SCANIA# apt install blender denemo gimp inkscape vlc
...
```
Where are the simple methods to install every dependencies to Blender n Denemo and why ‘dictionaries-common’ n ‘libgtk-3-bin’ wasnt installed using both direct (# apt install dictionaries-common libgtk-3-bin) n ‘-f’ (# apt install -f) shells of installations?

---

### Post by ian-weisser on 2016-09-12
Apt is not complaining to you about some arcane dependency problem what can be fixed with just the right apt-voodoo.
You (not apt) have created a version conflict that impossible for apt to resolve. You (not apt) must make an Executive Decision. 

Usually, this is caused by installing non-Ubuntu software.
The simplest method to permanently fix the problem is to downgrade back to a stock-Ubuntu system, and rethink exactly which non-Ubuntu software you really need.
To downgrade, uninstall ALL non-Ubuntu software, then disable the non-Ubuntu sources (including PPAs), then clean out your package cache, then rebuild your apt package database (because your sources changed). If apt still errors at that point, please show us the new errors.

Er, one assumes you know how to do all that without more detail...because you are running as root. And root know all...and never makes typos or mistakes.

If you try to force-install, you may (or may not) irreparably break your system. At that point, our best advice would be to reinstall.

> [COLOR=#000000][FONT=&amp]410 not fully installed or removed.[/FONT][/COLOR]
This means you created the conflict and broke your package manager a long time ago. You are not receiving security updates.

---

### Post by hd.scania on 2016-09-13
```
root@HD-SCANIA# apt remove gimp inkscape vlc winehq-devel
root@HD-SCANIA# ls /var/lib/apt/lists
archives.ubuntu.com.Xenial.Xerus.resources.00.deb
archives.ubuntu.com.Xenial.Xerus.resources.01.deb
archives.ubuntu.com.Xenial.Xerus.resources.02.deb
...
archives.ubuntu.com.Xenial.Xerus.resources.ff.deb
archives.ubuntu.com.Xenial.Xerus.security.00.deb
archives.ubuntu.com.Xenial.Xerus.security.01.deb
archives.ubuntu.com.Xenial.Xerus.security.02.deb
...
archives.ubuntu.com.Xenial.Xerus.security.ff.deb
archives.ubuntu.com.Xenial.Xerus.updates.00.deb
archives.ubuntu.com.Xenial.Xerus.updates.01.deb
archives.ubuntu.com.Xenial.Xerus.updates.02.deb
...
archives.ubuntu.com.Xenial.Xerus.updates.ff.deb
status
root@HD-SCANIA# cd /var/lib/apt/lists
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.resources.4b.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.security.4b.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.3d.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.3f.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.42.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.47.deb
root@HD-SCANIA/var/lib/apt/lists# rm -rf archives.ubuntu.com.Xenial.Xerus.updates.4b.deb
root@HD-SCANIA/var/lib/apt/lists# cd /media/hd_scania
root@HD-SCANIA# apt install blender denemo gimp inkscape vlc
...
```
After the problematic packages BOLDED in RED have been removed on terminal shells by this morning, the apps are begun regularly installed and results are below.
The external apps that i install from terminal shells are just Gimp, Inkscape, VLC, WineHQ, that WineHQ is the only app under the PPA repositories for me having no ideas to unbundle it on terminal shells.
```
root@HD-SCANIA:/home/hd_scania# apt install gimp inkscape vlc blender denemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ...
Suggested packages:
  ...
The following NEW packages will be installed:
  acl adduser adwaita-icon-theme alsa-base alsa-utils apt apt-utils aspell aspell-en at-spi2-core blender blender-data ca-certificates
  cgmanager colord colord-data coreutils cpp cpp-5 curl ... xterm zip zlib1g
0 upgraded, 794 newly installed, 0 to remove and 0 not upgraded.
Need to get 471 MB of archives.
After this operation, 1,817 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 gcc-6-base amd64 6.0.1-0ubuntu1 [14.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libc6 amd64 2.23-0ubuntu3 [2,584 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgcc1 amd64 1:6.0.1-0ubuntu1 [38.5 kB]                                             
...                                                         
Get:794 http://archive.ubuntu.com/ubuntu xenial/main amd64 libauthen-sasl-perl all 2.1600-1 [48.7 kB]                                         
Fetched 471 MB in 2h 12min 3s (59.5 kB/s)                                                                                                     
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 3%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 7%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 11%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Extracting templates from packages: 100%
root@HD-SCANIA:/home/hd_scania# apt install debconf && apt install gimp inkscape vlc blender denemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adduser apt apt-utils debconf-i18n debianutils dpkg gcc-5-base gcc-6-base gnupg gpgv init-system-helpers libacl1 libapt-inst2.0
  libapt-pkg5.0 libattr1 libaudit-common libaudit1 libbz2-1.0 libc6 libdb5.3 libgcc1 liblocale-gettext-perl liblz4-1 liblzma5 libpam-modules
  libpam-modules-bin libpam0g libpcre3 libreadline6 libselinux1 libsemanage-common libsemanage1 libsepol1 libstdc++6 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtinfo5 libusb-0.1-4 libustr-1.0-1 lsb-base multiarch-support passwd perl-base readline-common
  sensible-utils tar ubuntu-keyring update-motd zlib1g
Suggested packages:
  perl-modules ecryptfs-utils aptitude | synaptic | wajig dpkg-dev apt-doc python-apt debconf-doc debconf-utils whiptail | dialog
  libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl perl libqtgui4-perl libqtcore4-perl gnupg-curl gnupg-doc libpcsclite1 parcimonie
  xloadimage | imagemagick | eog glibc-doc locales libpam-doc readline-doc bzip2 ncompress xz-utils tar-scripts
The following NEW packages will be installed:
  adduser apt apt-utils debconf debconf-i18n debianutils dpkg gcc-5-base gcc-6-base gnupg gpgv init-system-helpers libacl1 libapt-inst2.0
  libapt-pkg5.0 libattr1 libaudit-common libaudit1 libbz2-1.0 libc6 libdb5.3 libgcc1 liblocale-gettext-perl liblz4-1 liblzma5 libpam-modules
  libpam-modules-bin libpam0g libpcre3 libreadline6 libselinux1 libsemanage-common libsemanage1 libsepol1 libstdc++6 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtinfo5 libusb-0.1-4 libustr-1.0-1 lsb-base multiarch-support passwd perl-base readline-common
  sensible-utils tar ubuntu-keyring update-motd zlib1g
0 upgraded, 51 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.0 MB of archives.
After this operation, 50.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 gcc-6-base amd64 6.0.1-0ubuntu1 [14.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libc6 amd64 2.23-0ubuntu3 [2,584 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgcc1 amd64 1:6.0.1-0ubuntu1 [38.5 kB]                                             
Get:4 http://archive.ubuntu.com/ubuntu xenial/main amd64 sensible-utils all 0.0.9 [10.5 kB]                                                   
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 debianutils amd64 4.7 [85.4 kB]                                                      
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbz2-1.0 amd64 1.0.6-8 [30.8 kB]                                                   
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbz2-1.0 amd64 1.0.6-8 [30.8 kB]                                                   
Err:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbz2-1.0 amd64 1.0.6-8                                                             
  Hash Sum mismatch
Get:7 http://archive.ubuntu.com/ubuntu xenial/main amd64 multiarch-support amd64 2.23-0ubuntu3 [6,824 B]                                      
...                                             
Get:51 http://archive.ubuntu.com/ubuntu xenial/main amd64 update-motd all 3.6-0ubuntu1 [5,378 B]                                              
Fetched 13.0 MB in 4min 14s (51.3 kB/s)                                                                                                       
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.6-8_amd64.deb  Hash Sum mismatch

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@HD-SCANIA:/home/hd_scania# apt update --fix-missing
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease                                                                                    
Hit:2 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease                                                                       
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Get:6 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [187 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [383 kB]                                                            
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [325 kB]                                                        
Get:10 http://archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages [55.3 kB]                                                     
Get:11 http://archive.ubuntu.com/ubuntu xenial-proposed/universe Translation-en [23.8 kB]                                                     
Get:12 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 DEP-11 Metadata [6,502 B]                                                  
Fetched 1,323 kB in 20s (66.0 kB/s)                                                                                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@HD-SCANIA:/home/hd_scania# apt install gimp inkscape vlc blender denemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ...
Suggested packages:
  ...
The following NEW packages will be installed:
  acl adduser adwaita-icon-theme alsa-base alsa-utils apt apt-utils aspell aspell-en at-spi2-core blender blender-data ca-certificates
  cgmanager colord colord-data coreutils cpp cpp-5 curl ... xterm zip zlib1g
0 upgraded, 794 newly installed, 0 to remove and 0 not upgraded.
Need to get 458 MB/471 MB of archives.
After this operation, 1,817 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 coreutils amd64 8.25-2ubuntu2 [1,175 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libbz2-1.0 amd64 1.0.6-8 [30.8 kB]                                                   
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 e2fslibs amd64 1.42.13-1ubuntu1 [188 kB]                                             
...
Get:172 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxcb-shape0 amd64 1.11.1-1ubuntu1 [5,756 B]                                      
Err:172 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxcb-shape0 amd64 1.11.1-1ubuntu1                                                
  Hash Sum mismatch
Get:173 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxcb-xkb1 amd64 1.11.1-1ubuntu1 [29.2 kB]                                        
...                                                          
Get:744 http://archive.ubuntu.com/ubuntu xenial/main amd64 libauthen-sasl-perl all 2.1600-1 [48.7 kB]                                         
Fetched 458 MB in 2h 19min 1s (54.9 kB/s)                                                                                                     
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.11.1-1ubuntu1_amd64.deb  Hash Sum mismatch

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@HD-SCANIA:/home/hd_scania#
```

---

