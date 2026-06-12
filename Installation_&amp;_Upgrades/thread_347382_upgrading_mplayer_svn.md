---
title: "upgrading mplayer svn"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by barnjo on 2007-01-27
Hi, I installed mplayer from svn and tried to play a 720p h264 mkv file without much luck.

I have since installed libmatroska, x264 and xvid from source, all of which seemed to work, updated my svn source files to a newer revision (don't know why, about 3 files got updated)

I reinstalled mplayer by

sudo make uninstall
./configure --enable-gui
make
sudo make install

But now it wont even open my matroska file.

anyone know what to do?

---

