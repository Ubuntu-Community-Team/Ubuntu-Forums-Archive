---
title: "ffmpeg question"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by 18rudi18 on 2010-03-19
ok i was trying to install libavcodec-unstripped-51 package so i could convert my videos so i could put them in my ipod. but when i tried to install it, this message appeared in my Package Installer "Dependency is not satisfiable: libx264-59 (>= 1:0.svn20080408 " 
how do fix it?

i've beet trying to convert my videos for days without any success...please help me im what you guys call a "noob"...haha

 i am using Ubuntu

---

### Post by bumanie on 2010-03-19
Install winff - it is a simple gui for ffmpeg - it's in the repo's. > sudo apt-get install winffIt does do h.264 compatible conversions.

---

### Post by 18rudi18 on 2010-03-20
i've tried that and it shows me this 

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (27956/583) -> 23.98 (24000/1001)
Input #0, matroska, from '/home/rudi/Videos/Zombieland.mkv':
  Duration: 01:22:51.77, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x536, PAR 1:1 DAR 160:67, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 24000 Hz, stereo, s16
    Stream #0.2: Subtitle: 0x0000
Unknown encoder 'libfaac'

---

### Post by Captain Giraffe on 2010-03-20
I also tried ffwin without success. Also made some attempts with vlc that worked out a lot better. Make sure to open the messages window and maybe increase the verbosity a notch to make sure you catch the messages. Media-> Convert / Save, add source file, Convert... then tweak the profile you need.

Or to maintain the same codecs used and just tweak it in size  I use ffmpeg with
```
ffmpeg -i Movie.mkv -sameq -s 340x200 -vcodec copy -scodec copy -acodec copy Movie.smaller.mkv

sameq(uality) s(ize) v(ideo)codec s(ubtitles)codec and a(udio)codec.

```

Good luck.

---

