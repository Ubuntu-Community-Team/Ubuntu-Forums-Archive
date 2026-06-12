---
title: "Elltube and Karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by the.lost.one on 2009-10-23
The youtube downloading client Elltube which was working fine on Jaunty and initially even on Karmic now does not convert the files to mp3 after downloading. Here is an error log of a sample file i was trying to convert

 p, li { white-space: pre-wrap; }  ```

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
 

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
 Input #0, flv, from 'ONE LESS LONELY GIRL Official Music Vide.flv':
   Duration: 00:03:54.93, start: 0.000000, bitrate: 313 kb/s
     Stream #0.0: Video: flv, yuv420p, 400x226, 257 kb/s, 29.92 tbr, 1k tbn, 1k tbc
     Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 56 kb/s
 Output #0, mp3, to 'ONE LESS LONELY GIRL Official Music Vide.mp3':
     Stream #0.0: Audio: 0x0000, 22050 Hz, stereo, s16, 64 kb/s
 Stream mapping:
   Stream #0.1 -> #0.0
 Unsupported codec for output stream #0.0
 
```

---

