---
title: "[SOLVED] Can't Install, What Am I Doing Wrong?"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Gewalop on 2008-06-21
Hi everybody

I Can't install any, ANY package

here's what I'm doing

i put the package here 

```
/media/disk/NewFolder/vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb[/code

and went to terminal
and

[code]drbat@Bat:~$ cd /media/disk/NewFolder
drbat@Bat:/media/disk/NewFolder$ sudo apt-get install vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386
```

I want to learn how to install from terminal, thanx

---

### Post by wormser on 2008-06-21
> **Gewalop said:**
> I want to learn how to install from terminal, thanx

Read this blog.  [How to Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Gewalop on 2008-06-21
first of all thanx

second, i DID what they said but didn't work

that's why i posted, to know what i'm doing wrong

---

### Post by wormser on 2008-06-21
> **Gewalop said:**
> sudo apt-get install vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386


It looks like you have the wrong package name.  Are you trying to install VLC?  That package name you have looks strange.  Is it something you downloaded?  The command apt-get goes onto the internet and downloads the files then installs them.  If you do not know the name you can search for the name with apt-cache search whatever.

```
apt-cache search vlc
dvd95 - DVD9 to DVD5 converter
getstream - DVB streaming application
hdhomerun-config - Configuration utility for Silicon Dust HD HomeRun
libvcdinfo-dev - library to extract information from VideoCD (development files)
libvcdinfo0 - library to extract information from VideoCD
mythbuntu-lirc-generator - Mythbuntu Lirc Configuration Generator
pidgin-mpris - sets your available message to your currently playing track
videolan-doc - documentation for the VideoLAN streaming solution
vls - lightweight MPEG and DVD video streaming server
freeplayer - wrapper around vlc for French ADSL FreeBox
libvlc0 - multimedia player and streamer library
libvlc0-dev - development files for VLC
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
**vlc - multimedia player and streamer**
vlc-nox - multimedia player and streamer (without X support)
vlc-plugin-alsa - dummy transitional package
vlc-plugin-arts - aRts audio output plugin for VLC
vlc-plugin-esd - Esound audio output plugin for VLC
vlc-plugin-ggi - GGI video output plugin for VLC
vlc-plugin-glide - Glide video output plugin for VLC
vlc-plugin-pulse - Pulseaudio audio output plugin for VLC
vlc-plugin-sdl - SDL video and audio output plugin for VLC
vlc-plugin-svgalib - SVGAlib video output plugin for VLC
wxvlc - dummy transitional package
x264 - video encoder for the H.264/MPEG-4 AVC standard
```If you want more details of the package use apt-cache show package-name.

```
apt-cache show vlc
Package: vlc
Priority: optional
Section: multiverse/graphics
Installed-Size: 3228
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>
Architecture: i386
Version: 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3
Replaces: vlc-aa (<< 0.5.0), vlc-lirc (<< 0.5.0), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-aa (<< 0.5.2-2), vlc-plugin-alsa (<< 0.8.5-test3.debian-4), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), wxvlc (<< 0.8.5-test3.debian-4)
Provides: mp3-decoder
Depends: libaa1 (>= 1.4p5), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcaca0 (>= 0.99.beta13b-1), libcairo2 (>= 1.6.0), libcdio7, libcucul0 (>= 0.99.beta13b-1), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfreetype6 (>= 2.3.5), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1-21), libgl1-mesa-glx | libgl1, libglib2.0-0, libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libiso9660-5, libjpeg62, libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libpango1.0-0 (>= 1.20.1), libpng12-0 (>= 1.2.13-4), libsdl-image1.2 (>= 1.2.5), libsdl1.2debian (>= 1.2.10-1), libsm6, libstdc++6 (>= 4.2.1-4), libtar, libtiff4, libvcdinfo0 (>> 0.7.23), libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1), libwxbase2.6-0 (>= 2.6.3.2.2), libwxgtk2.6-0 (>= 2.6.3.2.2), libx11-6, libxext6, libxinerama1, libxosd2 (>= 2.2.13), libxv1, ttf-dejavu, vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3), vlc-plugin-pulse, zlib1g (>= 1:1.2.3.3.dfsg-1)
Recommends: videolan-doc
Suggests: mozilla-plugin-vlc
Conflicts: vlc-aa (<< 0.5.0), vlc-lirc (<< 0.5.0), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-aa (<< 0.5.2-2), vlc-plugin-alsa (<< 0.8.5-test3.debian-4), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), wxvlc (<< 0.8.5-test3.debian-4)
Filename: pool/multiverse/v/vlc/vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
Size: 1140014
MD5sum: 397fad7555fceb1a7895d4f8e493c3fb
SHA1: 6c65f83bd599df95cb9d666c5315e9ce4d6ea59b
SHA256: a420222b123d9f0c805dd6c0d474f56f69b449eb8eeab299df5f31e1f8fcc70c
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-esd, vlc-plugin-sdl,
 vlc-plugin-arts, vlc-plugin-pulse) or video plugins (vlc-plugin-sdl,
 vlc-plugin-ggi, vlc-plugin-glide, vlc-plugin-svgalib). There is also a web
 browser plugin in the mozilla-plugin-vlc package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```Now, if you want to install it use sudo apt-get install package-name.

```
sudo apt-get install vlc
```Read through that link I gave you again.  Sometime new things take a few reads to sink in.  It will teach you how to install with apt-get, .debs and source.

BTW, the Installation & Upgrades is for installing Ubuntu.  Questions like this should be in the beginner section.  You will get faster responses there.

---

### Post by kevmitch on 2008-06-21
> **Gewalop said:**
> Hi everybody
```
drbat@Bat:~$ cd /media/disk/NewFolder
drbat@Bat:/media/disk/NewFolder$ sudo apt-get install vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386

```


Since you have a .deb package file that you want to install, you would use the command 

dpkg -i vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb

You would usually only do it this way, however if said package was not available through the usual repositories and you had to download it from the web. If you wanted to install vlc form the repositories, you would run

[CODE]apt-get install vlc[\CODE]

---

### Post by Gewalop on 2008-06-21
> Since you have a .deb package file that you want to install, you would use the command

dpkg -i vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb

You would usually only do it this way, however if said package was not available through the usual repositories and you had to download it from the web. If you wanted to install vlc form the repositories, you would run

[code]apt-get install vlc[\CODE]

Thank you big time.
Solved!

---

