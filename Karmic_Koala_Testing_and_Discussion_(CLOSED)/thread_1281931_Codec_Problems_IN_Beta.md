---
title: "Codec Problems IN Beta"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BAMF1501 on 2009-10-03
Ok so i installed the beta last night clean partion. But i'm having some issues with codecs , i installed vlc player like normal but when i go to play a video file it says cannot play due to no xvid codec etc... why is this happening ? I have all codecs installed and all the unrestricted stuff and still gives same issue :(

---

### Post by blakamin on 2009-10-03
[http://ubuntuforums.org/showthread.php?t=1281039]("http://ubuntuforums.org/showthread.php?t=1281039")

---

### Post by BAMF1501 on 2009-10-03
i tried ubuntu-restricted-extras, still dont work

---

### Post by blakamin on 2009-10-03
Did you try the libavcodec? it fixed mine.

---

### Post by BAMF1501 on 2009-10-03
when i install  libavcodec it removes vlc and my xvid cap :(

---

### Post by blakamin on 2009-10-03
hmmm.. thats really weird... when you reinstall vlc does it remove libavcodec?
I did this on alpha 5 and my vlc is still running (have to output to openGL tho because it'll crash otherwise)

---

### Post by BAMF1501 on 2009-10-03
OK now i reinstalled vlc and it plays media but looks like this wtf lol

[IMG]http://i33.tinypic.com/2146nph.png[/IMG]

---

### Post by blakamin on 2009-10-03
try changing the output under tools>preferences>video to openGL or something other than X

[SIZE="1"]
edit:good movie BTW, might want to adjust your screenshot so I cant read it at the bottom :D[/SIZE]

---

### Post by BAMF1501 on 2009-10-03
tried still dont work :(

---

### Post by blakamin on 2009-10-03
Bugga, i've run out of ideas. sorry.

---

### Post by mc4man on 2009-10-03
Try something first to get out of the way. Start vlc like this to reset

```
vlc --reset-config --reset-plugins-cache
```

if no better (or worse, if that's possible ) then close out and restart with 
```
vlc -vv > vlc_output.log 2>&1
```

Play a file for a few secs., close out and look thru log for anything useful ( log is in home folder, and will usually be large

A lot of the log isn't needed, anything from before vlc started playing file can usually be ignored

Ex. 
you're probably interested in what is below this last line ( all of the below just reflects vlc starting

> doug@doug-desktop:~$ vlc -vv
VLC media player 1.0.3-git Goldeneye
[0x80af140] main libvlc debug: VLC media player - version 1.0.3-git Goldeneye - (c) 1996-2009 the VideoLAN team
[0x80af140] main libvlc debug: libvlc was configured with ./configure  ' --with-tuning=native' '--prefix=/usr' '--config-cache' '--enable-loader' '--disable-schroedinger' '--enable-fast-install' '--with-binary-version=1ubuntu1' '--disable-update-check' '--disable-fb' '--enable-cddax' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-lirc' '--enable-a52' '--enable-snapshot' '--enable-aa' '--enable-dvbpsi' '--disable-fluidsynth' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--enable-real' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--with-live555-tree=/usr/lib/live' '--enable-svgalib'  'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x80af140] main libvlc debug: translation test: code is "C"
[0x80af140] main libvlc debug: checking plugin modules
[0x80af140] main libvlc debug: loading plugins cache file /home/doug/.cache/vlc/plugins-04041e.dat
[0x80af140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x80af140] main libvlc debug: module bank initialized (385 modules)
[0x80af140] main libvlc debug: opening config file (/home/doug/.config/vlc/vlcrc)
[0x80af140] main libvlc debug: No Media Player is running. Continuing normally.
[0x80af140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x80af140] main libvlc debug: looking for memcpy module: 3 candidates
[0x80af140] main libvlc debug: using memcpy module "memcpymmxext"
[0x8161b20] main input debug: Creating an input for 'Media Library'
[0x8161b20] main input debug: Input is a meta file: disabling unneeded options
[0x8161b20] main input debug: using timeshift granularity of 50 MBytes
[0x8161b20] main input debug: using timeshift path '/tmp'
[0x8161b20] main input debug: `file/xspf-open:///home/doug/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/doug/.local/share/vlc/ml.xspf'
[0x8161b20] main input debug: creating demux: access='file' demux='xspf-open' path='/home/doug/.local/share/vlc/ml.xspf'
[0x81443e0] main demux debug: looking for access_demux module: 1 candidate
[0x81443e0] main demux warning: no access_demux module matching "file" could be loaded
[0x81443e0] main demux debug: TIMER module_need() : 1.298 ms - Total 1.298 ms / 1 intvls (Avg 1.298 ms)
[0x8161b20] main input debug: creating access 'file' path='/home/doug/.local/share/vlc/ml.xspf'
[0x8166e80] main access debug: looking for access module: 3 candidates
[0x8166e80] access_file access debug: opening file `/home/doug/.local/share/vlc/ml.xspf'
[0x8166e80] main access debug: using access module "access_file"
[0x8166e80] main access debug: TIMER module_need() : 1.745 ms - Total 1.745 ms / 1 intvls (Avg 1.745 ms)
[0x81645e8] main stream debug: Using AStream*Stream
[0x81645e8] main stream debug: pre buffering
[0x81645e8] main stream debug: received first data after 0 ms
[0x81645e8] main stream debug: pre-buffering done 296 bytes in 0s - 8029 kbytes/s
[0x8144de8] main stream debug: looking for stream_filter module: 4 candidates
[0x8144de8] main stream debug: TIMER module_need() : 1.265 ms - Total 1.265 ms / 1 intvls (Avg 1.265 ms)
[0x814abd8] main stream debug: looking for stream_filter module: 1 candidate
[0x814abd8] main stream debug: using stream_filter module "stream_filter_record"
[0x814abd8] main stream debug: TIMER module_need() : 0.548 ms - Total 0.548 ms / 1 intvls (Avg 0.548 ms)
[0x8161b20] main input debug: creating demux: access='file' demux='xspf-open' path='/home/doug/.local/share/vlc/ml.xspf'
[0x814afb0] main demux debug: looking for demux module: 1 candidate
[0x814afb0] playlist demux debug: using XSPF playlist reader
[0x814afb0] main demux debug: using demux module "playlist"
[0x814afb0] main demux debug: TIMER module_need() : 0.896 ms - Total 0.896 ms / 1 intvls (Avg 0.896 ms)
[0x8161b20] main input debug: `file/xspf-open:///home/doug/.local/share/vlc/ml.xspf' successfully opened
[0x814a3b0] main xml debug: looking for xml module: 2 candidates
[0x814a3b0] main xml debug: using xml module "xml"
[0x814a3b0] main xml debug: TIMER module_need() : 1.198 ms - Total 1.198 ms / 1 intvls (Avg 1.198 ms)
[0x814afb0] playlist demux debug: parsed 0 tracks successfully
[0x814a3b0] main xml debug: removing module "xml"
[0x8161b20] main input debug: EOF reached
[0x814afb0] main demux debug: removing module "playlist"
[0x814abd8] main stream debug: removing module "stream_filter_record"
[0x8166e80] main access debug: removing module "access_file"
[0x8161b20] main input debug: TIMER input launching for 'Media Library' : 18.808 ms - Total 18.808 ms / 1 intvls (Avg 18.808 ms)
[0x814b140] main playlist debug: rebuilding array of current - root Playlist
[0x814b140] main playlist debug: rebuild done - 0 items, index -1
[0x814b140] main playlist debug: Activated
[0x8164f98] main interface debug: looking for interface module: 1 candidate
[0x8164f98] main interface debug: using interface module "hotkeys"
[0x8164f98] main interface debug: TIMER module_need() : 0.818 ms - Total 0.818 ms / 1 intvls (Avg 0.818 ms)
[0x8164f98] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8164470] main interface debug: looking for interface module: 1 candidate
[0x8164f98] main interface debug: thread started
[0x8164470] main interface debug: using interface module "dbus"
[0x8164470] main interface debug: TIMER module_need() : 9.600 ms - Total 9.600 ms / 1 intvls (Avg 9.600 ms)
[0x8164470] main interface debug: thread started
[0x8164470] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x81451f0] main interface debug: looking for interface module: 1 candidate
[0x81451f0] main interface debug: using interface module "inhibit"
[0x81451f0] main interface debug: TIMER module_need() : 0.562 ms - Total 0.562 ms / 1 intvls (Avg 0.562 ms)
[0x81451f0] main interface debug: thread started
[0x81451f0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8164908] main interface debug: looking for interface module: 1 candidate
[0x8164908] main interface debug: using interface module "screensaver"
[0x8164908] main interface debug: TIMER module_need() : 0.550 ms - Total 0.550 ms / 1 intvls (Avg 0.550 ms)
[0x8164908] main interface debug: thread started
[0x8164908] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x80af2d8] main interface debug: looking for interface module: 1 candidate
[0x80af2d8] main interface debug: using interface module "signals"
[0x80af2d8] main interface debug: TIMER module_need() : 0.638 ms - Total 0.638 ms / 1 intvls (Avg 0.638 ms)
[0x80af2d8] main interface debug: thread started
[0x80af2d8] main interface debug: thread ended
[0x80af2d8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x8159b30] main interface debug: looking for interface module: 1 candidate
[0x8159b30] main interface debug: using interface module "globalhotkeys"
[0x8159b30] main interface debug: TIMER module_need() : 36.945 ms - Total 36.945 ms / 1 intvls (Avg 36.945 ms)
[0x8159b30] main interface debug: thread started
[0x8159b30] main interface debug: thread ended
[0x8159b30] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x80af140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x815be00] main interface debug: looking for interface module: 4 candidates
[0x815be00] qt4 interface debug: Error while initializing qt-specific localization
[0x815be00] main interface debug: using interface module "qt4"
[0x815be00] main interface debug: TIMER module_need() : 277.020 ms - Total 277.020 ms / 1 intvls (Avg 277.020 ms)
[0x815be00] main interface debug: thread started
[0x815be00] main interface debug: thread ended
[0x815be00] [COLOR="Blue"]main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)[/COLOR]


edit:
A while i don't know if it matters here you should be using the  "extra" versions of at least libavcodec52, libavformat52, libpostproc51, and libswscale0

search ffmpeg in synaptic and ck.

If not,** don't mark the existing ones for removal**, just mark all the "extra" versiona for install and apply

---

