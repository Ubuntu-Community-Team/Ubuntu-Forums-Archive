---
title: "ffmpeg with mp3"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-03-07
I followed the instruction of [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)


added lame and libvpbx
added them to the config:

> cd
git clone git://git.ffmpeg.org/ffmpeg.git
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc \
    --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb \
    --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid \
    --enable-x11grab --enable-libvpx --enable-libmp3lame
make
sudo checkinstall --pkgname=ffmpeg --pkgversion="5:$(./version.sh)" --backup=no \
    --deldoc=yes --default
hash x264 ffmpeg ffplay ffprobe

... and when I am finished I try to check it:

ffmpeg -formats|grep mp3
FFmpeg version git-f4f4e12, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  7 2011 18:32:10 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
 DE mp3             MPEG audio layer 3


What do I miss?

---

### Post by andrew.46 on 2011-03-08
Try the following:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep mp3[/COLOR]**
FFmpeg version git-6a7e074, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  8 2011 09:03:45 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-nonfree --enable-gpl --enable-version3
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**[COLOR="Red"]  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)[/COLOR]**
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3adufloat     ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3float        MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mp3on4float     MP3onMP4

```

Andrew

---

### Post by ELMIT on 2011-03-08
Andrew, thank you very much.

I have in some directories a couple of *.mp4 files and want to convert them to mp3, so that I can put them on my mp3 player. Any version of code I found on the Interenet I tried failed. What is the proper way?

THanks again!

bye

Ronald

---

### Post by andrew.46 on 2011-03-08
Hi Ronald,

Well, that all depends a little on the actual makeup of your mp4 files. Can you post the results of the following command with one of your files as follows:

```
ffmpeg -i *my_file.mp4*
```

obviously substituting the name of your own file for *my_file.mp4*. It will then be an easy matter to suggest suitable syntax to transcode your files :).

Andrew

---

### Post by ELMIT on 2011-03-08
Andrew,

thank you again for your help.

Here is the output:

ffmpeg -i abc_prac_1.mp4 
FFmpeg version git-f4f4e12, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  7 2011 18:32:10 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0

[mov,mp4,m4a,3gp,3g2,mj2 @ 0x32415b0] max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (2997/100)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'abc_prac_1.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 1
    compatible_brands: mp42mp41
    creation_time   : 2010-05-22 19:56:36
  Duration: 00:49:36.05, start: 0.000000, bitrate: 1158 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 1080x720 [PAR 1:1 DAR 3:2], 1061 kb/s, 29.97 fps, 29.97 tbr, 2997 tbn, 1k tbc
    Metadata:
      creation_time   : 2010-05-22 19:56:36
    Stream #0.1(eng): Audio: aac, 44100 Hz, stereo, s16, 55 kb/s
    Metadata:
      creation_time   : 2010-05-22 19:56:36
    Stream #0.2(eng): Data: mp4s / 0x7334706D
    Metadata:
      creation_time   : 2010-05-22 19:56:36
    Stream #0.3(eng): Data: mp4s / 0x7334706D
    Metadata:
      creation_time   : 2010-05-22 19:56:36
    Stream #0.4(eng): Data: rtp  / 0x20707472, 8 kb/s
    Metadata:
      creation_time   : 2010-05-22 19:56:36
    Stream #0.5(eng): Data: rtp  / 0x20707472, 27 kb/s
    Metadata:
      creation_time   : 2010-05-22 19:56:36
At least one output file must be specified



bye

Ronald

---

### Post by andrew.46 on 2011-03-08
Hi Ronald,

I note that your FFmpeg details do not seem to include *--enable-libmp3lame*, have you included this in your ./configure options? In the guide you have followed this must be done manually, as noted in Step 5. If all is done then the following is one way of converting this particular file:

```

ffmpeg -i abc_prac_1.mp4 -vn -acodec libmp3lame -ab 55k test.mp3

```

Other options include use of the -aq option instead of bitrate, piping to lame and attempting to copy meta information as well. But this commandline should hopefully get things started :).

Andrew

---

### Post by ELMIT on 2011-03-08
Andrew,

that is exactly what I found, it does not include the
--enable-libvpx --enable-libmp3lame

even I added it!!!!

That is what I am exactly using in step 7!!!

> cd
git clone git://git.ffmpeg.org/ffmpeg.git
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc \
    --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb \
    --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid \
    --enable-x11grab --enable-libvpx --enable-libmp3lame
make
sudo checkinstall --pkgname=ffmpeg --pkgversion="5:$(./version.sh)" --backup=no \
    --deldoc=yes --default
hash x264 ffmpeg ffplay ffprobe

---

### Post by ELMIT on 2011-03-08
Andrew,

I started over with step 1 ~ 8 and it is now working.

Thanks!

---

### Post by andrew.46 on 2011-03-08
Great news Ronald :).

---

