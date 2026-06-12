---
title: "Mplayer won't open at all"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2009-10-10
Ok does anyone esle have this problem?  im trying to play a video file, avi encoded in xvid format, and mplayer won't even load.

VLC attempts to open it but won't open the video portion...just audio

Movie player doesn't even get close.

Has there been regressions on the the video playback function that has been missed?

I tried to open it injaunty and it opens just fine....so it isn't the avi file that is corrupt or anything

Thanks in advance guys

---

### Post by hikaricore on 2009-10-10
Open it from a terminal window and look for any error output:

> mplayer filename.avi

---

### Post by Vanishing on 2009-10-10
> **firstc624 said:**
> Ok does anyone esle have this problem?  im trying to play a video file, avi encoded in xvid format, and mplayer won't even load.

VLC attempts to open it but won't open the video portion...just audio

Movie player doesn't even get close.

Has there been regressions on the the video playback function that has been missed?

I tried to open it injaunty and it opens just fine....so it isn't the avi file that is corrupt or anything

Thanks in advance guys
No problem here, maybe try to reinstall mplayer and related libs?:)

---

### Post by firstc624 on 2009-10-10
mplayer: symbol lookup error: mplayer: undefined symbol: codec_wav_tags

this is output from terminal when i try to play it

---

### Post by cariboo on 2009-10-10
Have you got the ubuntu-restricted-extras meta package installed?

---

### Post by mc4man on 2009-10-11
It may prove useful if you post whether you're using the karmic repo ffmpeg libs or did you install from some other means.

If using the karmic repo versions, then  which are installed - libavodec52 or libavcodec-extra-52, libavformat52 or libavformat-extra-52, ect. ect.

Both the repo mplayer and a vlc from anywhere use the system ffmpeg libs.

It also wouldn't hurt to say if you're using an mplayer or vlc from other than the karmic repo's  if that's the case.

To some degree the error suggests an incompatibility between mplayer and the installed ffmpeg libs


Starting vlc from the terminal as such and then attempting playback would give you some useful info ( and a whole lot more, the 1st. 90 lines probably won't matter here
```

vlc -vv
```

---

### Post by firstc624 on 2009-10-11
Sorry...

Yes i am using the official repos to install both mplayer and vlc.

Here is the output of the code vlc -vv....i just put all of it  cause i didnt know which would be valuable or not.

> firstc624@firstc624-laptop:~$ vlc -vv
VLC media player 1.0.2 Goldeneye
[0x13d8888] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x13d8888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu1' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x13d8888] main libvlc debug: translation test: code is "C"
[0x13d8888] main libvlc debug: checking plugin modules
[0x13d8888] main libvlc debug: loading plugins cache file /home/firstc624/.cache/vlc/plugins-04081e.dat
[0x13d8888] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x13d8888] main libvlc debug: module bank initialized (378 modules)
[0x13d8888] main libvlc debug: opening config file (/home/firstc624/.config/vlc/vlcrc)
[0x13d8888] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[0x13d8888] main libvlc debug: looking for memcpy module: 3 candidates
[0x13d8888] main libvlc debug: using memcpy module "memcpymmxext"
[0x14cb048] main input debug: Creating an input for 'Media Library'
[0x14cb048] main input debug: Input is a meta file: disabling unneeded options
[0x14cb048] main input debug: using timeshift granularity of 50 MBytes
[0x14cb048] main input debug: using timeshift path '/tmp'
[0x14cb048] main input debug: `file/xspf-open:///home/firstc624/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/firstc624/.local/share/vlc/ml.xspf'
[0x14cb048] main input debug: creating demux: access='file' demux='xspf-open' path='/home/firstc624/.local/share/vlc/ml.xspf'
[0x14d5b48] main demux debug: looking for access_demux module: 1 candidate
[0x14d5b48] main demux warning: no access_demux module matching "file" could be loaded
[0x14d5b48] main demux debug: TIMER module_need() : 0.453 ms - Total 0.453 ms / 1 intvls (Avg 0.453 ms)
[0x14cb048] main input debug: creating access 'file' path='/home/firstc624/.local/share/vlc/ml.xspf'
[0x14e6268] main access debug: looking for access module: 3 candidates
[0x14e6268] access_file access debug: opening file `/home/firstc624/.local/share/vlc/ml.xspf'
[0x14e6268] main access debug: using access module "access_file"
[0x14e6268] main access debug: TIMER module_need() : 0.343 ms - Total 0.343 ms / 1 intvls (Avg 0.343 ms)
[0x14e5008] main stream debug: Using AStream*Stream
[0x14e5008] main stream debug: pre buffering
[0x14e5008] main stream debug: received first data after 0 ms
[0x14e5008] main stream debug: pre-buffering done 296 bytes in 0s - 15213 kbytes/s
[0x14e5498] main stream debug: looking for stream_filter module: 4 candidates
[0x14e5498] main stream debug: TIMER module_need() : 0.316 ms - Total 0.316 ms / 1 intvls (Avg 0.316 ms)
[0x14ea9a8] main stream debug: looking for stream_filter module: 1 candidate
[0x14ea9a8] main stream debug: using stream_filter module "stream_filter_record"
[0x14ea9a8] main stream debug: TIMER module_need() : 0.102 ms - Total 0.102 ms / 1 intvls (Avg 0.102 ms)
[0x14cb048] main input debug: creating demux: access='file' demux='xspf-open' path='/home/firstc624/.local/share/vlc/ml.xspf'
[0x14e8cf8] main demux debug: looking for demux module: 1 candidate
[0x14e8cf8] playlist demux debug: using XSPF playlist reader
[0x14e8cf8] main demux debug: using demux module "playlist"
[0x14e8cf8] main demux debug: TIMER module_need() : 0.174 ms - Total 0.174 ms / 1 intvls (Avg 0.174 ms)
[0x14cb048] main input debug: `file/xspf-open:///home/firstc624/.local/share/vlc/ml.xspf' successfully opened
[0x14e9958] main xml debug: looking for xml module: 2 candidates
[0x14e9958] main xml debug: using xml module "xtag"
[0x14e9958] main xml debug: TIMER module_need() : 0.529 ms - Total 0.529 ms / 1 intvls (Avg 0.529 ms)
[0x14e8cf8] playlist demux debug: parsed 0 tracks successfully
[0x14e9958] main xml debug: removing module "xtag"
[0x14cb048] main input debug: EOF reached
[0x14e8cf8] main demux debug: removing module "playlist"
[0x14ea9a8] main stream debug: removing module "stream_filter_record"
[0x14e6268] main access debug: removing module "access_file"
[0x14cb048] main input debug: TIMER input launching for 'Media Library' : 3.592 ms - Total 3.592 ms / 1 intvls (Avg 3.592 ms)
[0x14c94c8] main playlist debug: Activated
[0x14c94c8] main playlist debug: rebuilding array of current - root Playlist
[0x14c94c8] main playlist debug: rebuild done - 0 items, index -1
[0x14e9bf8] main interface debug: looking for interface module: 1 candidate
[0x14e9bf8] main interface debug: using interface module "hotkeys"
[0x14e9bf8] main interface debug: TIMER module_need() : 0.193 ms - Total 0.193 ms / 1 intvls (Avg 0.193 ms)
[0x14e9bf8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x14e9bf8] main interface debug: thread started
[0x14cb3c8] main interface debug: looking for interface module: 1 candidate
[0x14cb3c8] main interface debug: using interface module "inhibit"
[0x14cb3c8] main interface debug: TIMER module_need() : 1.000 ms - Total 1.000 ms / 1 intvls (Avg 1.000 ms)
[0x14cb3c8] main interface debug: thread started
[0x14cb3c8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x14d3ca8] main interface debug: looking for interface module: 1 candidate
[0x14d3ca8] main interface debug: using interface module "screensaver"
[0x14d3ca8] main interface debug: TIMER module_need() : 0.186 ms - Total 0.186 ms / 1 intvls (Avg 0.186 ms)
[0x14d3ca8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x13d8ad8] main interface debug: looking for interface module: 1 candidate
[0x13d8ad8] main interface debug: using interface module "signals"
[0x13d8ad8] main interface debug: TIMER module_need() : 0.177 ms - Total 0.177 ms / 1 intvls (Avg 0.177 ms)
[0x13d8ad8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x13d9188] main interface debug: looking for interface module: 0 candidates
[0x13d9188] main interface error: no interface module matched "globalhotkeys,none"
[0x13d9188] main interface debug: TIMER module_need() : 0.062 ms - Total 0.062 ms / 1 intvls (Avg 0.062 ms)
[0x13d9188] main interface error: no suitable interface module
[0x13d8888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x13d8888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x13d9278] main interface debug: looking for interface module: 4 candidates
[0x14d3ca8] main interface debug: thread started
[0x13d8ad8] main interface debug: thread started
[0x13d8ad8] main interface debug: thread ended
[0x13d9278] qt4 interface debug: Error while initializing qt-specific localization
[0x13d9278] main interface debug: using interface module "qt4"
[0x13d9278] main interface debug: TIMER module_need() : 202.330 ms - Total 202.330 ms / 1 intvls (Avg 202.330 ms)
[0x13d9278] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x13d9278] main interface debug: thread started
[0x13d9278] main interface debug: thread ended
[0x14c94c8] main playlist debug: adding item `Fringe.avi' ( /home/firstc624/Desktop/Fringe.avi )
[0x13d9278] qt4 interface debug: Adding a new MRL to recent ones: /home/firstc624/Desktop/Fringe.avi
[0x14c94c8] main playlist debug: rebuilding array of current - root Playlist
[0x14c94c8] main playlist debug: rebuild done - 1 items, index -1
[0x14c94c8] main playlist debug: processing request item Fringe.avi node null skip 0
[0x14c94c8] main playlist debug: resyncing on Fringe.avi
[0x14c94c8] main playlist debug: Fringe.avi is at 0
[0x14c94c8] main playlist debug: starting new item
[0x14c94c8] main playlist debug: creating new input thread
[0x7ffa1c001e28] main input debug: Creating an input for 'Fringe.avi'
[0x7ffa1c001e28] main input debug: thread started
[0x7ffa1c001e28] main input debug: using timeshift granularity of 50 MBytes
[0x7ffa1c001e28] main input debug: using timeshift path '/tmp'
[0x7ffa1c001e28] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x13d9278] qt4 interface debug: IM: Setting an input
[0x7ffa1c001e28] main input debug: `/home/firstc624/Desktop/Fringe.avi' gives access `' demux `' path `/home/firstc624/Desktop/Fringe.avi'
[0x7ffa1c001e28] main input debug: creating demux: access='' demux='' path='/home/firstc624/Desktop/Fringe.avi'
[0x1875c98] main demux debug: looking for access_demux module: 7 candidates
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x1875c98] main demux debug: TIMER module_need() : 133.786 ms - Total 133.786 ms / 1 intvls (Avg 133.786 ms)
[0x7ffa1c001e28] main input debug: creating access '' path='/home/firstc624/Desktop/Fringe.avi'
[0x1924f28] main access debug: looking for access module: 7 candidates
[0x1924f28] vcd access debug: trying .cue file: /home/firstc624/Desktop/Fringe.cue
[0x1924f28] vcd access debug: could not find .cue file
[0x1924f28] access_file access debug: opening file `/home/firstc624/Desktop/Fringe.avi'
[0x1924f28] main access debug: using access module "access_file"
[0x1924f28] main access debug: TIMER module_need() : 83.681 ms - Total 83.681 ms / 1 intvls (Avg 83.681 ms)
[0x1875c98] main stream debug: Using AStream*Stream
[0x1875c98] main stream debug: pre buffering
[0x1875c98] main stream debug: received first data after 12 ms
[0x1875c98] main stream debug: pre-buffering done 1024 bytes in 0s - 79 kbytes/s
[0x17fef68] main stream debug: looking for stream_filter module: 4 candidates
[0x17fef68] main stream debug: TIMER module_need() : 0.322 ms - Total 0.322 ms / 1 intvls (Avg 0.322 ms)
[0x17fef68] main stream debug: looking for stream_filter module: 1 candidate
[0x17fef68] main stream debug: using stream_filter module "stream_filter_record"
[0x17fef68] main stream debug: TIMER module_need() : 0.213 ms - Total 0.213 ms / 1 intvls (Avg 0.213 ms)
[0x7ffa1c001e28] main input debug: creating demux: access='' demux='' path='/home/firstc624/Desktop/Fringe.avi'
[0x19ef6e8] main demux debug: looking for demux module: 51 candidates
[0x17fef68] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:733522084 pos:0
[0x17fef68] avi stream debug: found LIST chunk: 'AVI '
[0x17fef68] avi stream debug: <list 'AVI '>
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8830 pos:12
[0x17fef68] avi stream debug: found LIST chunk: 'hdrl'
[0x17fef68] avi stream debug: <list 'hdrl'>
[0x17fef68] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x17fef68] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 640x352
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4244 pos:88
[0x17fef68] avi stream debug: found LIST chunk: 'strl'
[0x17fef68] avi stream debug: <list 'strl'>
[0x17fef68] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x17fef68] avi stream debug: strh: type:vids handler:0x64697678 samplesize:0 23.98fps
[0x17fef68] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x17fef68] avi stream debug: strf: video:XVID 640x352 planes:1 12bpp
[0x17fef68] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:212
[0x17fef68] avi stream debug: </list 'strl'>
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4234 pos:4340
[0x17fef68] avi stream debug: found LIST chunk: 'strl'
[0x17fef68] avi stream debug: <list 'strl'>
[0x17fef68] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4352
[0x17fef68] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 41.67fps
[0x17fef68] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4416
[0x17fef68] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 0bits/sample 125kb/s
[0x17fef68] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4120 pos:4454
[0x17fef68] avi stream debug: </list 'strl'>
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:260 pos:8582
[0x17fef68] avi stream debug: found LIST chunk: 'odml'
[0x17fef68] avi stream debug: <list 'odml'>
[0x17fef68] avi stream debug: found Chunk fourcc:686c6d64 (dmlh) size:248 pos:8594
[0x17fef68] avi stream warning: unknown chunk (not loaded)
[0x17fef68] avi stream debug: </list 'odml'>
[0x17fef68] avi stream debug: </list 'hdrl'>
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:28 pos:8850
[0x17fef68] avi stream debug: found LIST chunk: 'INFO'
[0x17fef68] avi stream debug: <list 'INFO'>
[0x17fef68] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:15 pos:8862
[0x17fef68] avi stream debug: ISFT: software : Nandub v1.0rc2
[0x17fef68] avi stream debug: </list 'INFO'>
[0x17fef68] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1346 pos:8886
[0x17fef68] avi stream debug: found Chunk fourcc:5453494c (LIST) size:728367740 pos:10240
[0x17fef68] avi stream debug: skipping movi chunk
[0x17fef68] avi stream debug: found Chunk fourcc:31786469 (idx1) size:5144096 pos:728377988
[0x17fef68] avi stream debug: idx1: index entry:321506
[0x17fef68] avi stream debug: </list 'AVI '>
[0x17fef68] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1868 pos:733522092
[0x17fef68] avi stream debug: * LIST-root size:733523968 pos:0
[0x17fef68] avi stream debug:      + RIFF-AVI  size:733522084 pos:0
[0x17fef68] avi stream debug:      |    + LIST-hdrl size:8830 pos:12
[0x17fef68] avi stream debug:      |    |    + avih size:56 pos:24
[0x17fef68] avi stream debug:      |    |    + LIST-strl size:4244 pos:88
[0x17fef68] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x17fef68] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x17fef68] avi stream debug:      |    |    |    + JUNK size:4120 pos:212
[0x17fef68] avi stream debug:      |    |    + LIST-strl size:4234 pos:4340
[0x17fef68] avi stream debug:      |    |    |    + strh size:56 pos:4352
[0x17fef68] avi stream debug:      |    |    |    + strf size:30 pos:4416
[0x17fef68] avi stream debug:      |    |    |    + JUNK size:4120 pos:4454
[0x17fef68] avi stream debug:      |    |    + LIST-odml size:260 pos:8582
[0x17fef68] avi stream debug:      |    |    |    + dmlh size:248 pos:8594
[0x17fef68] avi stream debug:      |    + LIST-INFO size:28 pos:8850
[0x17fef68] avi stream debug:      |    |    + ISFT size:15 pos:8862
[0x17fef68] avi stream debug:      |    + JUNK size:1346 pos:8886
[0x17fef68] avi stream debug:      |    + LIST-movi size:728367740 pos:10240
[0x17fef68] avi stream debug:      |    + idx1 size:5144096 pos:728377988
[0x17fef68] avi stream debug:      + JUNK size:1868 pos:733522092
[0x19ef6e8] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED 
[0x19ef6e8] avi demux debug: stream[0] rate:24000 scale:1001 samplesize:0
[0x19ef6e8] avi demux debug: stream[0] video(XVID) 640x352 12bpp 23.976025fps
[0x7ffa1c001e28] main input debug: selecting program id=0
[0x19ef6e8] avi demux debug: stream[1] rate:48000 scale:1152 samplesize:0
[0x19ef6e8] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 0bits
[0x19ef6e8] avi demux debug: stream[0] created 117431 index entries
[0x19ef6e8] avi demux debug: stream[1] created 204075 index entries
[0x19ef6e8] avi demux debug: stream[0] length:4897 (based on index)
[0x19ef6e8] avi demux debug: stream[1] length:4897 (based on index)
[0x19ef6e8] main demux debug: using demux module "avi"
[0x19ef6e8] main demux debug: TIMER module_need() : 270.510 ms - Total 270.510 ms / 1 intvls (Avg 270.510 ms)
[0x7ffa1c001e28] main input debug: looking for a subtitle file in /home/firstc624/Desktop/
[0x7ffa1c01a578] main decoder debug: looking for decoder module: 31 candidates
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x7ffa1c01a578] avcodec decoder debug: libavcodec initialized (interface 0x341400)
[0x7ffa1c01a578] avcodec decoder debug: using direct rendering
[0x7ffa1c01a578] avcodec decoder error: cannot open codec (MPEG-4 Video)
[0x7ffa1c01a578] main decoder debug: TIMER module_need() : 173.255 ms - Total 173.255 ms / 1 intvls (Avg 173.255 ms)
[0x7ffa1c01a578] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
[0x7ffa1c01a578] main decoder debug: killing decoder fourcc `XVID', 0 PES in FIFO
[0x1a5a0b8] main decoder debug: looking for decoder module: 31 candidates
[0x1a5a0b8] main decoder debug: using decoder module "mpeg_audio"
[0x1a5a0b8] main decoder debug: TIMER module_need() : 0.261 ms - Total 0.261 ms / 1 intvls (Avg 0.261 ms)
[0x1a5a0b8] main decoder debug: thread started
[0x1a5a0b8] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x7ffa1c001e28] main input debug: `/home/firstc624/Desktop/Fringe.avi' successfully opened
[0x7ffa1c001e28] main input debug: Buffering 0%
[0x7ffa1c001e28] main input debug: Buffering 8%
[0x7ffa1c001e28] main input debug: Buffering 16%
[0x7ffa1c001e28] main input debug: Buffering 25%
[0x7ffa1c001e28] main input debug: Buffering 33%
[0x7ffa1c001e28] main input debug: Buffering 41%
[0x7ffa1c001e28] main input debug: Buffering 50%
[0x7ffa1c001e28] main input debug: Buffering 58%
[0x7ffa1c001e28] main input debug: Buffering 66%
[0x7ffa1c001e28] main input debug: Buffering 75%
[0x7ffa1c001e28] main input debug: Buffering 83%
[0x7ffa1c001e28] main input debug: Buffering 91%
[0x7ffa1c001e28] main input debug: Buffering 100%
[0x7ffa1c001e28] main input debug: Stream buffering done (325 ms in 0 ms)
[0x1a5a0b8] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:128
[0x7ffa1c001e28] main input debug: creating aout
[0x1a66768] main audio output debug: looking for audio output module: 4 candidates
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: New caching: 100
[0x13d9278] qt4 interface debug: New caching: 100
[0x1a66768] alsa audio output debug: opening ALSA device `default'
[0x1a66768] main audio output debug: thread started
[0x1a66768] main audio output debug: thread (aout) created at priority 15 (alsa.c:687)
[0x1a66768] main audio output debug: using audio output module "alsa"
[0x1a66768] main audio output debug: TIMER module_need() : 935.057 ms - Total 935.057 ms / 1 intvls (Avg 935.057 ms)
[0x1a66768] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0x1a66768] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0x1a66768] main audio output debug: no need for any filter
[0x1a66768] main audio output debug: looking for audio mixer module: 3 candidates
[0x1a66768] main audio output debug: using audio mixer module "float32_mixer"
[0x1a66768] main audio output debug: TIMER module_need() : 8.697 ms - Total 8.697 ms / 1 intvls (Avg 8.697 ms)
[0x1a66768] main audio output debug: input 'mpga' 48000 Hz Stereo frame=1152 samples/969 bytes
[0x3438b08] main audio filter debug: looking for audio filter module: 1 candidate
[0x3438b08] scaletempo audio filter warning: bad input or output format
[0x3438b08] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x3438b08] main audio filter debug: TIMER module_need() : 12.088 ms - Total 12.088 ms / 1 intvls (Avg 12.088 ms)
[0x3438b08] main audio filter debug: looking for audio filter module: 1 candidate
[0x3438b08] scaletempo audio filter debug: format: 48000 rate, 2 nch, 4 bps, fl32
[0x3438b08] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x3438b08] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0x3438b08] main audio filter debug: using audio filter module "scaletempo"
[0x3438b08] main audio filter debug: TIMER module_need() : 0.743 ms - Total 0.743 ms / 1 intvls (Avg 0.743 ms)
[0x1a66768] main audio output debug: filter(s) 'mpga'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[0x34533b8] main audio output debug: looking for audio filter module: 24 candidates
[0x34533b8] main audio output debug: using audio filter module "mpgatofixed32"
[0x34533b8] main audio output debug: TIMER module_need() : 74.689 ms - Total 74.689 ms / 1 intvls (Avg 74.689 ms)
[0x1a66768] main audio output debug: found a filter for the whole conversion
[0x1a66768] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[0x3457dc8] main audio output debug: looking for audio filter module: 24 candidates
[0x3457dc8] main audio output debug: using audio filter module "bandlimited_resampler"
[0x3457dc8] main audio output debug: TIMER module_need() : 1.929 ms - Total 1.929 ms / 1 intvls (Avg 1.929 ms)
[0x1a66768] main audio output debug: found a filter for the whole conversion
[0x1a5a0b8] main decoder debug: End of audio preroll
[0x7ffa1c001e28] main input debug: Decoder buffering done in 1035 ms
[0x1a66768] main audio output warning: PTS is out of range (-7549), dropping buffer
[0x1a66768] main audio output warning: PTS is out of range (-31497), dropping buffer
[0x1a66768] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0x13d8888] main libvlc debug: deactivating the playlist
[0x14c94c8] main playlist debug: Deactivate
[0x14c94c8] main playlist debug: incoming request - stopping current input
[0x14c94c8] main playlist debug: dying input
[0x7ffa1c001e28] main input debug: control type=0
[0x7ffa1c001e28] main input debug: control: stopping input
[0x14c94c8] main playlist debug: dying input
[0x1a5a0b8] main decoder debug: removing module "mpeg_audio"
[0x1a5a0b8] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[0x34533b8] main audio output debug: removing module "mpgatofixed32"
[0x3438b08] main audio filter debug: removing module "scaletempo"
[0x3457dc8] main audio output debug: removing module "bandlimited_resampler"
[0x1a66768] main audio output debug: thread ended
[0x1a66768] main audio output debug: removing module "alsa"
[0x1a66768] main audio output debug: removing module "float32_mixer"
[0x7ffa1c001e28] main input debug: releasing aout
[0x17fef68] avi stream debug: free chunk avih
[0x17fef68] avi stream debug: free chunk strh
[0x17fef68] avi stream debug: free chunk strf
[0x17fef68] avi stream debug: free chunk JUNK
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream debug: free chunk strh
[0x17fef68] avi stream debug: free chunk strf
[0x17fef68] avi stream debug: free chunk JUNK
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream warning: unknown chunk (not unloaded)
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream debug: free chunk ISFT
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream debug: free chunk JUNK
[0x17fef68] avi stream debug: free chunk LIST
[0x17fef68] avi stream debug: free chunk idx1
[0x17fef68] avi stream debug: free chunk RIFF
[0x17fef68] avi stream debug: free chunk JUNK
[0x17fef68] avi stream debug: free chunk LIST
[0x19ef6e8] main demux debug: removing module "avi"
[0x17fef68] main stream debug: removing module "stream_filter_record"
[0x1924f28] main access debug: removing module "access_file"
[0x7ffa1c001e28] main input debug: Program doesn't contain anymore ES
[0x7ffa1c001e28] main input debug: thread ended
[0x14c94c8] main playlist debug: dead input
[0x13d9278] qt4 interface debug: IM: Deleting the input
[0x13d9278] qt4 interface debug: Updating the geometry
[0x13d9278] qt4 interface debug: Updating the geometry
[0x7ffa1c001e28] main input debug: TIMER input launching for 'Fringe.avi' : 679.201 ms - Total 679.201 ms / 1 intvls (Avg 679.201 ms)
[0x14c94c8] main playlist debug: saving Media Library to file /home/firstc624/.local/share/vlc/ml.xspf
[0x14c94c8] main playlist debug: looking for playlist export module: 1 candidate
[0x14c94c8] main playlist debug: using playlist export module "export"
[0x14c94c8] main playlist debug: TIMER module_need() : 0.406 ms - Total 0.406 ms / 1 intvls (Avg 0.406 ms)
[0x14c94c8] main playlist debug: removing module "export"
[0x14c94c8] main playlist debug: Deactivated
[0x13d8888] main libvlc debug: removing all services discovery tasks
[0x13d8888] main libvlc debug: removing all interfaces
[0x13d9278] qt4 interface debug: Quitting the Qt4 Interface
[0x13d9278] qt4 interface debug: destroying the main Qt4 interface
[0x13d9278] qt4 interface debug: Destroying the main interface
[0x13d9278] main interface debug: removing module "qt4"
[0x13d8ad8] main interface debug: removing module "signals"
[0x14d3ca8] main interface debug: removing module "screensaver"
[0x14cb3c8] main interface debug: removing module "inhibit"
[0x14e9bf8] main interface debug: removing module "hotkeys"
[0x13d8888] main libvlc debug: removing playlist
[0x14c94c8] main playlist debug: Destroyed
[0x13d8888] main libvlc debug: TIMER ML Load : Total 4.298 ms / 1 intvls (Avg 4.298 ms)
[0x13d8888] main libvlc debug: TIMER Items array build : Total 0.108 ms / 2 intvls (Avg 0.054 ms)
[0x13d8888] main libvlc debug: TIMER ML Dump : Total 0.551 ms / 1 intvls (Avg 0.551 ms)
[0x13d8888] main libvlc debug: removing stats
[0x13d8888] main libvlc debug: removing module "memcpymmxext"
[0x13d8888] main libvlc debug: opening config file (/home/firstc624/.config/vlc/vlcrc)
[0x13d8888] main libvlc debug: writing plugins cache /home/firstc624/.cache/vlc/plugins-04081e.dat


---

### Post by mc4man on 2009-10-11
your problem (for both players) is this

> 0x7ffa1c01a578] avcodec decoder debug: libavcodec initialized (interface 0x341400)
[0x7ffa1c01a578] avcodec decoder debug: using direct rendering
[0x7ffa1c01a578] avcodec decoder error: cannot open codec (MPEG-4 Video)
[0x7ffa1c01a578] main decoder debug: TIMER module_need() : 173.255 ms - Total 173.255 ms / 1 intvls (Avg 173.255 ms)
[0x7ffa1c01a578] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.

> [QUOTE]then which are installed - libavcodec52 or libavcodec-extra-52, libav...
.........?[/QUOTE]

Edit 
make sure the 'extra' versions are installed ( cob't mark existing for removal, just mark the extra for install and apply

---

### Post by Vanishing on 2009-10-11
> **firstc624 said:**
> Ok does anyone esle have this problem?  im trying to play a video file, avi encoded in xvid format, and mplayer won't even load.

VLC attempts to open it but won't open the video portion...just audio

Movie player doesn't even get close.

Has there been regressions on the the video playback function that has been missed?

I tried to open it injaunty and it opens just fine....so it isn't the avi file that is corrupt or anything

Thanks in advance guys
actually, when i tried it again, apparently mkv file cannot be played. the error output is:
> MPlayer interrupted by signal 11 in module: video_read_frame
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
i tried to change the audio driver to alsa, and used -nosound,then i got the following:
> MPlayer interrupted by signal 11 in module: video_read_frame
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

o.o
weird

---

### Post by mc4man on 2009-10-11
> actually, when i tried it again, apparently mkv file cannot be played. the error output is:

I could be wrong because I wasn't paying close attention but on my testing install i believe that the repo mplayer was initially built for karmic using gcc-4.3.3
It's now showing gcc-4.4.1

see here (post 252
[http://ubuntuforums.org/showthread.php?t=1081070&page=26](http://ubuntuforums.org/showthread.php?t=1081070&page=26)

and this how-to ( and or file a bug report
[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

---

### Post by Vanishing on 2009-10-11
> **mc4man said:**
> I could be wrong because I wasn't paying close attention but on my testing install i believe that the repo mplayer was initially built for karmic using gcc-4.3.3
It's now showing gcc-4.4.1

see here (post 252
[http://ubuntuforums.org/showthread.php?t=1081070&page=26](http://ubuntuforums.org/showthread.php?t=1081070&page=26)

and this how-to ( and or file a bug report
[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)
thank you..gonna try it now.:guitar:

---

### Post by Vanishing on 2009-10-11
> **Vanishing said:**
> thank you..gonna try it now.:guitar:

It worked!!
Thank you!:popcorn:

---

### Post by andrew.46 on 2009-10-12
Hi Vanishing,

> **Vanishing said:**
> It worked!!

The guide for compiling your own MPlayer solved the problem?

Andrew

---

