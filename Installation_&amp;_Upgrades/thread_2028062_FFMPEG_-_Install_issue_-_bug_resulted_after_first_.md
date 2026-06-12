---
title: "FFMPEG - Install issue - bug resulted after first use"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by spindler on 2012-07-17
I installed FFMPEG using the following instructions. 

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

I am using this software package with DRUPAL 7.  I could not use the instruction for FFMPEG as described in the document page above.  I had to load FFMPEG using the apt-get istall ppmpeg command.   This worked to install it and DRUPAL was able to find it.

I attempted to load a video on my website and FFMPEG was suppose to convert it from .mov to fv4.

I got an error:

[HTML]
FFmpeg failed to transcode test_video.mov.

**Reported errors**



PHPVideoToolkit  Error: Execute error. Output for file  "/home/website/sites/default/files/videos/original/test_video.mov"  was not found. Please check server write permissions and/or available  codecs compiled with FFmpeg. You can check the encode decode  availability by inspecting the output array from  PHPVideoToolkit::getFFmpegInfo().   **Executed commands and output**



 /usr/bin/ffmpeg -i '/home/website/sites/default/files/videos/original/test_video.mov' -s '640x360'  sites/default/temp/1342509155-50051063bbd2d. 
ffmpeg version 0.7.6-4:0.7.6-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers 
  built on Jun 12 2012 16:28:10 with gcc 4.6.1 
  configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static 
  WARNING: library configuration mismatch 
  avutil      configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay  
 avcodec     configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay 
  avformat    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay  
 avdevice    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay  
 avfilter    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay  
 swscale     configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay  
 postproc    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay 
  libavutil    51.  7. 0 / 51.  7. 0 
  libavcodec   53.  6. 0 / 53.  6. 0  
 libavformat  53.  3. 0 / 53.  3. 0 
  libavdevice  53.  0. 0 / 53.  0. 0 
  libavfilter   2.  4. 0 /  2.  4. 0 
  libswscale    2.  0. 0 /  2.  0. 0 
  libpostproc  52.  0. 0 / 52.  0. 0 
Seems stream 0 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1) 
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/website/sites/default/files/videos/original/test_video.mov': 
  Metadata: 
    major_brand     : qt 
    minor_version   : 537199360 
    compatible_brands: qt 
    creation_time   : 2012-07-16 21:32:29 
  Duration: 00:00:15.20, start: 0.000000, bitrate: 4761 kb/s 
    Stream #0.0(eng): Video: h264 (Main), yuv420p, 960x540, 3346 kb/s, 25 fps, 25 tbr, 2500 tbn, 5k tbc 
    Metadata: 
      creation_time   : 2012-07-16 21:32:29 
    Stream #0.1(eng): Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s 
    Metadata: 
      creation_time   : 2012-07-16 21:32:29 
Home directory /var/www not ours. 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM sites/default/temp/1342509155-50051063bbd2d. 
[alsa @ 0x9b345a0] cannot open audio device sites/default/temp/1342509155-50051063bbd2d. (No such file or directory) 
Output #0, alsa, to 'sites/default/temp/1342509155-50051063bbd2d.': 
  Metadata: 
    major_brand     : qt 
    minor_version   : 537199360 
    compatible_brands: qt 
    creation_time   : 2012-07-16 21:32:29 
    encoder         : Lavf53.3.0 
    Stream #0.0(eng): Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s 
    Metadata: 
      creation_time   : 2012-07-16 21:32:29 
Stream mapping: 
  Stream #0.1 -> #0.0 
Could not write header for output file #0 (incorrect codec parameters ?) [/HTML]


TROUBLESHOOTING I DID.

I check the file permissions in the /home/www/website/sites/default/files/videos/original/ and all of these files have a 777 permission.

So I am sure I am having an issue with the install of FFMPEG.

1.  Can someone tell me how to " inspecting the output array from  PHPVideoToolkit::getFFmpegInfo()"  ?

2. What library mismatch could there be?    I see a reference to library mismatch but i do not know what to do with this information. 

3. Any idea what librarys or codecs I need to install to fix this issue?

Any help ?

Thanks,

Spindler

---

