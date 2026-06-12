---
title: "VLC compile error?   no sout mux module matched &quot;mpeg&quot;"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-10-04
trying to stream using mpeg1 with VLC gives me this error
I CAN use all the other formats such as mpeg-TS, mpeg-PS, mp4, ogg, wmv.
SO can anyone tell me why mpeg1 does not work?
Was the VLC in the repos not compiled properly?


```

[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000418] main mux error: no sout mux module matched "mpeg"
[00000414] stream_out_standard stream out error: no suitable sout mux module for `file/mpeg:///home/scott/adaptecTV/testmpeg1'
[00000419] v4l2 demux error: cannot open video device (No such file or directory)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM  
[00000419] v4l2 demux error: cannot open device   for ALSA audio (No such file or directory)
[00000419] v4l2 demux error: cannot open device   for OSS audio (No such file or directory)
[00000419] v4l2 demux error: device does not support streaming i/o
[00000422] v4l2 access error: cannot open video device (No such file or directory)
ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[00000502] alsa audio output error: unable to commit hardware configuration (Input/output error)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1




```

---

### Post by plun on 2008-10-04
With Mplayers sample its ok for me

[http://samples.mplayerhq.hu/MPEG1/zelda%20first%20commercial.mpeg](http://samples.mplayerhq.hu/MPEG1/zelda%20first%20commercial.mpeg)


```
plun@Plun:~$ **vlc http://samples.mplayerhq.hu/MPEG1/zelda%20first%20commercial.mpeg**

VLC media player 0.9.3 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.3 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1

```

ffmpeg was also upgraded today.

---

### Post by sdowney717 on 2008-10-04
YES, that plays fine. except of course audio is messed up again.

I run into a problem when streaming a video and saving it to a file using the mpeg1 option.
I can stream and save all the formats except mpeg1.


```

[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[00000479] alsa audio output error: unable to commit hardware configuration (Input/output error)
[00000479] oss audio output error: cannot open audio device (/dev/dsp)
scott@scott-desktop:~$ 


```

---

### Post by Nullack on 2008-10-04
Mplayer is better because it has static links to the ffmpeg library at compile time. The VLC build in Intrepid uses an old fmpeg revision.

---

### Post by sdowney717 on 2008-10-05
I discovered the mpeg-ps format is what you want to use if you are going to burn a DVD

dvdstyler only recognizes mpeg-PS which is the DVD mpeg2 format

I had saved a stream as an mp4 file and then had to convert it using devede to mp2. That cost 4 hours of time. Next time I will just save as mpeg-PS.


The converted file went from mp4 (4.4gb) to mpeg2 (3,8 gb)
so mpeg2 is more compression? or did devede do so some type of adjustment to disk. it was at 99% disk usage.

---

