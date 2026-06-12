---
title: "What is the version of ffmpeg in Ubuntu 10.10?"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2010-10-28
Hi, all:

I'm wondering what is the version of ffmpeg in Ubuntu 10.10's default repository??

I'm currently using Ubuntu 10.04, and the default ffmpeg in Ubuntu 10.04's repository is of the version:

>   libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0

which is a bit old.
I'm wondering if Ubuntu 10.10's default ffmpeg is of version 0.6.1? 

Thanks in advance.

Best Regards
Jia

---

### Post by SecretCode on 2010-10-28
0.6-4:0.6-2ubuntu6

```
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
FFmpeg 0.6-4:0.6-2ubuntu6
libavutil     50.15. 1 / 50.15. 1
libavcodec    52.72. 2 / 52.72. 2
libavformat   52.64. 2 / 52.64. 2
libavdevice   52. 2. 0 / 52. 2. 0
libavfilter    1.19. 0 /  1.19. 0
libswscale     0.11. 0 /  0.11. 0
libpostproc   51. 2. 0 / 51. 2. 0

```

Note that it's not built with the libamr so can't be used for mobile phone recordings. Apparently amr/3GPP is not free software.

---

### Post by andrew.46 on 2010-10-28
Hi Secret,

> **SecretCode said:**
> Note that it's not built with the libamr so can't be used for mobile phone recordings. Apparently amr/3GPP is not free software.

Mind you FFmpeg can be built against opencore-amr which is free and available in the Ubuntu Repositories, for those not keen to compile Medibuntu can help out with a [libavcodec-extra-52]("http://packages.medibuntu.org/maverick/libavcodec-extra-52.html") package that has been compiled against libopencore-amr.

Andrew

---

### Post by jiapei100 on 2010-10-28
The problem is I found the problem of ffmpeg,

[http://ffmpeg-users.933282.n4.nabble.com/FFmpeg-Last-Frame-td2256146.html](http://ffmpeg-users.933282.n4.nabble.com/FFmpeg-Last-Frame-td2256146.html)

last frame missing for when encoding .mpg 

Besides, unicap also depends on ffmpeg. Well, anyway, without a better(newer) ffmpeg, I've got to rebuild loads of packages which depend on ffmpeg.

So, now, upgrading to 10.10 right away.

Cheers both.

Best Regards
JIA

---

