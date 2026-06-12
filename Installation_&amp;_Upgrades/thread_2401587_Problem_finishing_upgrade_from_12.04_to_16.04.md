---
title: "Problem finishing upgrade from 12.04 to 16.04"
date: 2018-09-19
forum: Installation &amp; Upgrades
---

### Post by loveland on 2018-09-19
Hi,
I was upgrading my system to Ubuntu 16.04 and during the screen to check the new .bashrc pressed a key combination that killed the upgrade screen session and upgrade in progress. Now, I can't finish the process.
Here is the end of the output I see when I run: sudo do-release-upgrade

```
Broken libdvdnav4:amd64 Breaks on mencoder [ amd64 ] < 2:1.0~rc4.dfsg1+svn34540-1+deb7u2build0.12.04.1 -> 2:1.2.1-1ubuntu1.1 > ( universe/video ) (< 2:1.0)
  Considering mencoder:amd64 0 as a solution to libdvdnav4:amd64 8
  Upgrading mencoder:amd64 due to Breaks field in libdvdnav4:amd64
Broken libdvdnav4:amd64 Breaks on mplayer [ amd64 ] < 2:1.0~rc4.dfsg1+svn34540-1+deb7u2build0.12.04.1 -> 2:1.2.1-1ubuntu1.1 > ( universe/video ) (< 2:1.0)
  Considering mplayer:amd64 1 as a solution to libdvdnav4:amd64 8
  Upgrading mplayer:amd64 due to Breaks field in libdvdnav4:amd64
Investigating (9) mplayer [ amd64 ] < 2:1.0~rc4.dfsg1+svn34540-1+deb7u2build0.12.04.1 -> 2:1.2.1-1ubuntu1.1 > ( universe/video )
Broken mplayer:amd64 Depends on libavcodec-ffmpeg56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavcodec-ffmpeg56:amd64 0 as a solution to mplayer:amd64 1
  Holding Back mplayer:amd64 rather than change libavcodec-ffmpeg56:amd64
Broken mplayer:amd64 Depends on libavcodec-ffmpeg-extra56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavcodec-ffmpeg-extra56:amd64 0 as a solution to mplayer:amd64 1
  Holding Back mplayer:amd64 rather than change libavcodec-ffmpeg-extra56:amd64
  Or group keep for mplayer:amd64
Broken mplayer:amd64 Depends on libavformat-ffmpeg56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavformat-ffmpeg56:amd64 0 as a solution to mplayer:amd64 1
  Holding Back mplayer:amd64 rather than change libavformat-ffmpeg56:amd64
Investigating (9) mencoder [ amd64 ] < 2:1.0~rc4.dfsg1+svn34540-1+deb7u2build0.12.04.1 -> 2:1.2.1-1ubuntu1.1 > ( universe/video )
Broken mencoder:amd64 Depends on libavcodec-ffmpeg56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavcodec-ffmpeg56:amd64 0 as a solution to mencoder:amd64 0
  Holding Back mencoder:amd64 rather than change libavcodec-ffmpeg56:amd64
Broken mencoder:amd64 Depends on libavcodec-ffmpeg-extra56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavcodec-ffmpeg-extra56:amd64 0 as a solution to mencoder:amd64 0
  Holding Back mencoder:amd64 rather than change libavcodec-ffmpeg-extra56:amd64
  Or group keep for mencoder:amd64
Broken mencoder:amd64 Depends on libavformat-ffmpeg56 [ amd64 ] < none -> 7:2.8.15-0ubuntu0.16.04.1 > ( universe/libs ) (>= 7:2.4)
  Considering libavformat-ffmpeg56:amd64 0 as a solution to mencoder:amd64 0
  Holding Back mencoder:amd64 rather than change libavformat-ffmpeg56:amd64
Done


Broken packages 


Your system contains broken packages that couldn't be fixed with this 
software. Please fix them first using synaptic or apt-get before 
proceeding. 




Preparing the upgrade failed 


Preparing the system for the upgrade failed so a bug reporting 
process is being started.

```
I'm not sure if this is due to the fact that I mistakenly killed the upgrade or if it's from prior bad installations. Mencoder and mplayer are older versions that I tried to install in the past and never got working correctly with my system. Today, I've tried removing them, but this didn't help. I also tried to fix dependencies by running: sudo apt-get install -f and see the following:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 python-scipy : Depends: libumfpack5.6.2 but it is not installable
 ubuntu-desktop : Depends: checkbox-gui but it is not installed
                  Depends: gnome-calculator but it is not installed
                  Depends: gstreamer1.0-alsa but it is not installed
                  Depends: gstreamer1.0-plugins-base-apps but it is not installed
                  Depends: ubuntu-session but it is not installed
                  Depends: ubuntu-settings but it is not installed
                  Depends: unity-control-center but it is not installed
                  Depends: unity-settings-daemon but it is not installed
                  Recommends: cheese but it is not installed
                  Recommends: fonts-lklug-sinhala but it is not installed
                  Recommends: fonts-sil-abyssinica but it is not installed
                  Recommends: fonts-sil-padauk but it is not installed
                  Recommends: fonts-tibetan-machine but it is not installed
                  Recommends: gnome-mahjongg but it is not installed
                  Recommends: libreoffice-ogltrans but it is not installed
                  Recommends: libreoffice-pdfimport but it is not installed
                  Recommends: libreoffice-presentation-minimizer but it is not installable
                  Recommends: python3-aptdaemon.pkcompat but it is not installed
                  Recommends: unity-webapps-common but it is not installed
                  Recommends: xul-ext-unity but it is not installable
                  Recommends: xul-ext-webaccounts but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
This looks more like a problem with the stopped upgrade to me... 
Please help!

Thank you
Anna

---

### Post by Impavidus on 2018-09-20
Well, that's a mess...

12.04 has been dead for a long time. The upgrade from 12.04 would lead to 14.04, which is still supported but so old that I wouldn't recommend anyone to begin using it now. 16.04 still has some life in it left, but the latest LTS release is 18.04. Fixing this mess and doing a number of release upgrades, fixing more mess inbetween and finally getting to the latest release is not the way to go. I suggest you backup your important documents (if you haven't done so already) and try a clean install of 18.04. That shouldn't take more than an hour.

---

