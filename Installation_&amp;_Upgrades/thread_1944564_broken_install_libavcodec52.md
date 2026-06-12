---
title: "broken install libavcodec52"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by kisugira on 2012-03-21
I dont know what to do with my broken install. libavcodec52

installed ```
avidemux glame uudeview ubuntu-restricted-extras mencoder mpeg2dec  tagtool easytag id3tool faac faad
...
....
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 libquicktime1
 mencoder
 libmjpegtools-1.9
 mjpegtools
 gstreamer0.10-plugins-bad-multiverse

```then i got 
```

~#mplayer 
mplayer: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory

```...
```

apt-get remove avidemux
The following packages have unmet dependencies:
  gstreamer0.10-ffmpeg: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not going to be installed or
                                 libavcodec-extra-52 (>= 4:0.5.1-1) but it is not going to be installed
  libavformat52: Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed or
                          libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.3) but it is not going to be installed
                 Depends: libavcodec52 (< 4:0.5.1-99) but it is not going to be installed or
                          libavcodec-extra-52 (< 4:0.5.1-99) but it is not going to be installed
  libquicktime1: Depends: libavcodec52 (>= 4:0.5+svn20090706-3) but it is not going to be installed or
                          libavcodec-extra-52 (>= 4:0.5+svn20090706-3) but it is not going to be installed
  mencoder: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not going to be installed or
                     libavcodec-extra-52 (>= 4:0.5.1-1) but it is not going to be installed
  mplayer: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.5.1-1) but it is not going to be installed
  vlc-nox: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.5.1-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```then i tried 
```
apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec52
The following NEW packages will be installed:
  libavcodec52
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/2,207kB of archives.
After this operation, 5,738kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158476 files and directories currently installed.)
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-ipod320.ffpreset', which is also in package ffmpeg 5:git-2012-03-20-9dd649c-1
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```:confused:

---

### Post by yeats on 2012-03-21
Try the steps listed here:

[http://ubuntuforums.org/showpost.php?p=5962046&postcount=9](http://ubuntuforums.org/showpost.php?p=5962046&postcount=9)

Then post back if that doesn't work.

---

### Post by kisugira on 2012-03-22
i tried but i dont know what should i remove

bob@bob-desktop:~$ sudo -s
[sudo] password for bob: 
root@bob-desktop:~# apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [57.3kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                             
Ign [http://ppa.launchpad.net/dreampie-devel/ppa/ubuntu/](http://ppa.launchpad.net/dreampie-devel/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg         
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg         
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [585kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [4,027B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [1,834B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [219kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [5,066B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [94.6kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [275kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Fetched 1,253kB in 3s (355kB/s)                     
Reading package lists... Done

root@bob-desktop:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

root@bob-desktop:~# apt-get clean

root@bob-desktop:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gstreamer0.10-ffmpeg: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not installed or
                                 libavcodec-extra-52 (>= 4:0.5.1-1) but it is not installed
  libavformat52: Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1.3) but it is not installed or
                          libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.3) but it is not installed
                 Depends: libavcodec52 (< 4:0.5.1-99) but it is not installed or
                          libavcodec-extra-52 (< 4:0.5.1-99) but it is not installed
  libquicktime1: Depends: libavcodec52 (>= 4:0.5+svn20090706-3) but it is not installed or
                          libavcodec-extra-52 (>= 4:0.5+svn20090706-3) but it is not installed
  mencoder: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not installed or
                     libavcodec-extra-52 (>= 4:0.5.1-1) but it is not installed
  mplayer: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not installed or
                    libavcodec-extra-52 (>= 4:0.5.1-1) but it is not installed
  vlc-nox: Depends: libavcodec52 (>= 4:0.5.1-1) but it is not installed or
                    libavcodec-extra-52 (>= 4:0.5.1-1) but it is not installed
E: Unmet dependencies. Try using -f.

root@bob-desktop:~# dpkg --remove -force --force-remove-reinstreq libavcodec52
dpkg: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

root@bob-desktop:~# dpkg --remove --force --force-remove-reinstreq libavcodec52
dpkg: unknown force/refuse option `--force-remove-reinstreq'

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

root@bob-desktop:~# dpkg --remove  --force-remove-reinstreq libavcodec52
dpkg: warning: ignoring request to remove libavcodec52, only the config
 files of which are on the system. Use --purge to remove them too.
root@bob-desktop:~# dpkg --purge  --force-remove-reinstreq libavcodec52
dpkg: dependency problems prevent removal of libavcodec52:
 mplayer depends on libavcodec52 (>= 4:0.5.1-1) | libavcodec-extra-52 (>= 4:0.5.1-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (>= 4:0.5.1-1ubuntu1.3) | libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.3); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.5.1-99) | libavcodec-extra-52 (<< 4:0.5.1-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (>= 4:0.5.1-1ubuntu1.3) | libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.3); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavformat52 depends on libavcodec52 (<< 4:0.5.1-99) | libavcodec-extra-52 (<< 4:0.5.1-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 vlc-nox depends on libavcodec52 (>= 4:0.5.1-1) | libavcodec-extra-52 (>= 4:0.5.1-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 4:0.5.1-1) | libavcodec-extra-52 (>= 4:0.5.1-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
dpkg: error processing libavcodec52 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 libavcodec52
root@bob-desktop:~# ?

---

### Post by kisugira on 2012-03-22
i did:

```
root@bob-desktop:~# dpkg --remove  --force-remove-reinstreq avidemux glame uudeview ubuntu-restricted-extras mencoder mpeg2dec  tagtool easytag id3tool faac faad
(Reading database ... 158475 files and directories currently installed.)
Removing avidemux ...
Removing glame ...
Removing uudeview ...
Removing ubuntu-restricted-extras ...
Removing mencoder ...
Removing mpeg2dec ...
Removing tagtool ...
Removing easytag ...
Removing id3tool ...
Removing faac ...
Removing faad ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for install-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
root@bob-desktop:~# mplayer
mplayer: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory
root@bob-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec52
The following NEW packages will be installed:
  libavcodec52
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 2,207kB of archives.
After this operation, 5,738kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libavcodec52 4:0.5.1-1ubuntu1.3 [2,207kB]
Fetched 2,207kB in 1s (1,153kB/s)       
Selecting previously deselected package libavcodec52.
(Reading database ... 158232 files and directories currently installed.)
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-ipod320.ffpreset', which is also in package ffmpeg 5:git-2012-03-20-9dd649c-1
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bob-desktop:~# mplayer 
mplayer: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory
root@bob-desktop:~# 

```

---

### Post by kisugira on 2012-03-22
removed ffmpeg (i compiled from git)
now i can install libavcodec52 !
mplayer works

```
root@bob-desktop:~/ffmpeg# dpkg -r ffmpeg
(Reading database ... 158231 files and directories currently installed.)
Removing ffmpeg ...
Processing triggers for man-db ...
root@bob-desktop:~/ffmpeg# apt-get install -f
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec52
The following NEW packages will be installed:
  libavcodec52
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 0B/2,207kB of archives.
After this operation, 5,738kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158029 files and directories currently installed.)
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb) ...
Setting up libavcodec52 (4:0.5.1-1ubuntu1.3) ...

Setting up libquicktime1 (2:1.1.4-1) ...

Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu3) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.18-0ubuntu1) ...
Setting up mjpegtools (1:1.9.0-0.5ubuntu3) ...
Ignoring install-info called from maintainer script
The package mjpegtools should be rebuilt with new debhelper to get trigger support

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@bob-desktop:~/ffmpeg# mplayer
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

```

---

### Post by kisugira on 2012-03-22
investigation:
before broken package, installed : avidemux glame uudeview ubuntu-restricted-extras mencoder mpeg2dec  tagtool easytag id3tool faac faad"
after broken libavcodec52 solved (see above) i can reinstall "avidemux glame uudeview ubuntu-restricted-extras mencoder mpeg2dec  tagtool easytag id3tool faac faad"
seems ubuntu-restricted-extras conflicted with git compided ffmpeg:

```
root@bob-desktop:~# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavcodec-extra-52
Suggested packages:
  libfaad0
The following packages will be REMOVED:
  libavcodec52
The following NEW packages will be installed:
  libavcodec-extra-52 ubuntu-restricted-extras
0 upgraded, 2 newly installed, 1 to remove and 7 not upgraded.
Need to get 2,224kB of archives.
After this operation, 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

