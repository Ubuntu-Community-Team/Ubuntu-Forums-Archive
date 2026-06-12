---
title: "vlc installation from source"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by hawas on 2008-10-03
Hi all
I´ve been trying to install vlc from the source code...that is essentially from this tar.gz file [http://linux.softpedia.com/progDownload/VLC-Download-2608.html](http://linux.softpedia.com/progDownload/VLC-Download-2608.html)

however while configuring it, I run into this error
....
checking for mad.h... yes
checking for mad_bit_init in -lmad... yes
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking for AVCODEC... no
configure: error: Could not find libavcodec or libavutil. Use --disable-avcodec to ignore this error.
See `config.log' for more details.

however, my computer says I have libavcodec already installed on my machine

 sudo apt-get install libavcodec0d
[sudo] password for hawas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec0d is already the newest version.
The following packages were automatically installed and are no longer required:
  procmail sensible-mda
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please help..some
P.S: I am a big time newbie.
_________________________________________________
To forgive is to suffer.

---

### Post by dualpretop on 2008-10-03
[http://ubuntuforums.org/showthread.php?t=935885&highlight=vlc](http://ubuntuforums.org/showthread.php?t=935885&highlight=vlc)

---

### Post by prostar on 2008-10-03
Install the "libavcodec-dev" package and try again...

---

