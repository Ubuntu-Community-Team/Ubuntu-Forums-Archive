---
title: "recordmydesktop and youtube"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by linden940 on 2010-04-17
the .ogv files wont upload right to youtube....when they are uploaded it looks like your on crack and all the colors are mixed together BUT when you play the ogv file ON your computer it looks fine...its clear...but if you change the format to anything else from ogv it will look like your on crack again EVEN if you play it ON your computer....

---

### Post by 0004tom on 2010-04-17
Convert the .ogv from gtk-recordmydesktop with mencoder 

```
mencoder out.ogv -o myvideo.avi -ovc lavc -oac mp3lame
```

something as simple as that will give you a relative small avi, and same quality as the output from gtk-recordmydesktop. You can also convert it with ffmpeg, but i prefer mencoder.

---

### Post by MacUntu on 2010-04-17
If you wanna try a different app, have a look at xvidcap.

---

### Post by linden940 on 2010-04-17
i have used ffmpeg and when i do...its looks like your on crack....its not a clear video

---

### Post by 0004tom on 2010-04-17
> **linden940 said:**
> i have used ffmpeg and when i do...its looks like your on crack....its not a clear video

Try mencoder thats how i do my screencasts then upload them to youtube.

---

### Post by linden940 on 2010-04-17
```
ubuntu@ubuntu-desktop:~$ mencoder 11.ogv -oac mp3lame -ovc lavc -o output_movie.avi 
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: '11.ogv'
Failed to open 11.ogv.
Cannot open file/device.

```

what am i doing wrong? 

lol never used mencoder...or not yet anyway

---

### Post by 0004tom on 2010-04-17
I'm to guess thats where 11.ogv is on your dekstop?

GTK-recordmydesktop dumps them in ~/

edit nvm i just noticed your in the home dir

---

### Post by linden940 on 2010-04-17
sure is

---

### Post by 0004tom on 2010-04-17
Just tried it here


```
 mencoder 11.ogv -oac mp3lame -ovc lavc -o output_movie.avi
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x1f0dc9
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  2560x1024  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:2560x1024  fps:15.000  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x1c7afc0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 2560 x 1024 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
videocodec: libavcodec (2560x1024 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   5.5s     83f (99%) 19.80fps Trem:   0min   0mb  A-V:0.038 [1330:72]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1330.628 kbit/s  (166328 B/s)  size: 920351 bytes  5.533 secs  83 frames

Audio stream:   72.913 kbit/s  (9114 B/s)  size: 45712 bytes  5.016 secs
```

works for me :s

---

### Post by linden940 on 2010-04-17
```
ubuntu@ubuntu-desktop:~$  mencoder 11.ogv -oac mp3lame -ovc lavc -o output_movie.avi
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: '11.ogv'
Failed to open 11.ogv.
Cannot open file/device.

Exiting...
ubuntu@ubuntu-desktop:~$ 

```


after you got it back to the avi...where you able to watch it?

any other ideas?

---

### Post by linden940 on 2010-04-17
this is what i get when i use winff

```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[ogg @ 0x171e480]Could not find codec parameters (Invalid Codec type -1)
Input #0, ogg, from '/home/ubuntu/Desktop/11.ogv':
  Duration: 00:00:02.60, start: 0.000000, bitrate: 1705 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1360x768, PAR 1:1 DAR 85:48, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22054 Hz, mono, s16, 89 kb/s
Output #0, flv, to '/dev/null':
    Stream #0.0: Video: flv (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, pass 1, 300 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
frame=   76 fps= 72 q=2.0 Lsize=       0kB time=2.54 bitrate=   0.0kbits/s    
video:221kB audio:0kB global headers:0kB muxing overhead -99.999558%
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[ogg @ 0x256c480]Could not find codec parameters (Invalid Codec type -1)
Input #0, ogg, from '/home/ubuntu/Desktop/11.ogv':
  Duration: 00:00:02.60, start: 0.000000, bitrate: 1705 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1360x768, PAR 1:1 DAR 85:48, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22054 Hz, mono, s16, 89 kb/s
Output #0, flv, to '/home/ubuntu/Desktop/11.flv':
    Stream #0.0: Video: flv (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, pass 2, 300 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libmp3lame, 22050 Hz, mono, s16, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
Press [q] to stop encoding
frame=   76 fps=  0 q=2.3 Lsize=     158kB time=2.46 bitrate= 526.1kbits/s    
video:138kB audio:17kB global headers:0kB muxing overhead 1.902803%
Press Enter to Continue

```


it makes it a flv or any other format JUST fine..but i cant watch it..it looks like your on crack...the colors are all f%$@ed up

---

### Post by linden940 on 2010-04-17
hey..I think I got it...I went looking and found this "transmageddon" (weird name) but it was able to change the format and have it play back *with out it looking like i was on crack..* so i'm going to try it and upload it to youtube to find out if it works or not.

---

### Post by linden940 on 2010-04-17
ok using the weird name program (Transmageddon)....it worked..uploaded a video and it uploaded the way it should of!

thanks for all of your help...only thing that has me...why is it working for one person but not others? there are other people that i have found that have the same problem anyway...its working now

---

