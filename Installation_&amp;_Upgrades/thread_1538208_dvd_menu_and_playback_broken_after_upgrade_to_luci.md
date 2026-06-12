---
title: "dvd menu and playback broken after upgrade to lucid"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by &lt;mike&gt; on 2010-07-24
Hi
Last night I upgraded to Lucid from Karmic, and now I can't play any DVDs (physical or ripped). These worked fine in Karmic, but now when I select them, playback freezes on any menu, and I have to kill the front end process.
Mythtv is set to use the internal player, but I have the same issue with VLC.

HELP!?!?!?

I use mythtv on the family tv, and my wife is about to kill me...

---

### Post by &lt;mike&gt; on 2010-07-25
Update:
I seem to have two or three different dvd issues...
Some dvds with menus won't play at all ... they crash the frontend (some with a segfault).
Here's an example debugging output from mythfrontend.real
```

2010-07-25 10:19:20.385 Leaving DVD Still Frame
2010-07-25 10:19:20.385 DVDNAV_SPU_CLUT_CHANGE happened.
2010-07-25 10:19:20.385 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, current_track==-1
2010-07-25 10:19:20.385 DVDNAV_AUDIO_STREAM_CHANGE: Current Active Stream 0
2010-07-25 10:19:20.386 ScreenSaverX11Private: StopTimer
2010-07-25 10:19:20.386 ScreenSaverX11Private: ResetTimer -- begin
2010-07-25 10:19:20.387 ScreenSaverX11Private: StopTimer
2010-07-25 10:19:20.387 ScreenSaverX11Private: StartTimer
2010-07-25 10:19:20.387 ScreenSaverX11Private: ResetTimer -- end
2010-07-25 10:19:20.389 AFD: HandleGopStart: gopset not set, syncing positionMap
2010-07-25 10:19:20.389 Dec: Resyncing position map. posmapStarted = 1 livetv(0) watchingRec(0)
2010-07-25 10:19:20.389 Entering DVD Still Frame
2010-07-25 10:19:20.390 DVD Playback Debugging: mpeg seq end 1  inDVDStill 1 decodeStillFrame 1
2010-07-25 10:19:20.390 [mpeg2video @ 0x7f3762c0e360]get_buffer() failed (stride changed)
2010-07-25 10:19:20.390 [mpeg2video @ 0x7f3762c0e360]get_buffer() failed (stride changed)
2010-07-25 10:19:20.390 AFD Error: Unknown decoding error
2010-07-25 10:19:20.390 DVD Playback Debugging inDVDMenu 0 storedPacketcount 0 dvdstill 1
2010-07-25 10:19:20.390 AFD: DVD Title Changed
2010-07-25 10:19:20.390 AFD: DVD Cell Changed. Update framesPlayed: 0 
2010-07-25 10:19:20.390 av_remove_stream 0x80
2010-07-25 10:19:20.391 av_remove_stream: no change to cur_st
2010-07-25 10:19:20.391 av_remove_stream: removing... s->nb_streams=2 i=1
2010-07-25 10:19:20.391 av_remove_stream: renumbering streams
2010-07-25 10:19:20.391 AFD: Stream #0, has id 0x1e0 codec id MPEG2VIDEO, type Video, bitrate 8000000 at 0x7f373c69c110
2010-07-25 10:19:20.391 AFD: Looking for decoder for MPEG2VIDEO
2010-07-25 10:19:20.391 RingBuf(/mnt/a/dvds/Little Einsteins/BigHugeAdventure): CalcReadAheadThresh(8000 KB)
			 -> threshhold(64 KB) min read(32 KB) blk size(128 KB)
2010-07-25 10:19:20.391 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-07-25 10:19:20.391 AO: Killing AudioOutputDSP
2010-07-25 10:19:20.392 AO: OutputAudioLoop: Stop Event
2010-07-25 10:19:20.392 AO: kickoffOutputAudioLoop exiting
2010-07-25 10:19:20.392 Setting IEC958 status: audio
2010-07-25 10:19:20.393 VideoOutputXv: InputChanged(720,576,1.33333) 'MPEG2'->'MPEG2'
2010-07-25 10:19:20.393 Display Rect  left: 0, top: 19, width: 900, height: 675, aspect: 1.26141
2010-07-25 10:19:20.393 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2010-07-25 10:19:20.393 Display Rect  left: 0, top: 19, width: 900, height: 675, aspect: 1.26141
2010-07-25 10:19:20.393 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2010-07-25 10:19:20.445 detectInterlace(Ignore Scan, Progressive Scan, 25, 576) ->Progressive Scan
2010-07-25 10:19:20.446 AFD Error: Bad stream (NULL)
2010-07-25 10:19:20.446 DVD Playback Debugging inDVDMenu 0 storedPacketcount 0 dvdstill 1
2010-07-25 10:19:20.446 DVD Playback Seek() time: 0; seekSpeed: 0
2010-07-25 10:19:20.446 DVDNAV_HOP_CHANNEL happened.
2010-07-25 10:19:20.446 DVDNAV_CELL_CHANGE: pg_length == 270000, pgc_length == 270000, cell_start == 0, pg_start == 0, title == 4, part == 1 titleParts 2
2010-07-25 10:19:20.446 Leaving DVD Still Frame
2010-07-25 10:19:20.446 DVDNAV_SPU_CLUT_CHANGE happened.
2010-07-25 10:19:20.446 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, current_track==-1
2010-07-25 10:19:20.446 DVDNAV_AUDIO_STREAM_CHANGE: Current Active Stream 0
2010-07-25 10:19:20.448 ScreenSaverX11Private: ResetTimer -- begin

```
(full log attached: crash frontend.zip - this one ended in a segmentation fault which is not recorded in the log, but which came up in the terminal window)

Others show a menu, but hang (either on a blank screen or on a static picture of the menu screen) after choosing an option. When running the frontend from a terminal, I got (over and over)
```

2010-07-25 21:49:42.383 AFD Error: Unknown decoding error
2010-07-25 21:49:42.383 DVD Playback Debugging inDVDMenu 0 storedPacketcount 1 dvdstill 0
2010-07-25 21:49:42.383 DVD Playback Debugging: mpeg seq end 0  inDVDStill 0 decodeStillFrame 0
2010-07-25 21:49:42.383 DVD Playback Debugging inDVDMenu 0 storedPacketcount 2 dvdstill 0
2010-07-25 21:49:42.383 DVD Playback Debugging: mpeg seq end 0  inDVDStill 0 decodeStillFrame 0
2010-07-25 21:49:42.383 [mpeg2video @ 0x7fc3673af360]get_buffer() failed (stride changed)

```
Some times, looking at the LCD, it looks as if the file is 'playing' but with no output... the screen is just black.
(full log attached: hang frontend.zip)

Some DVDs will actually play, but the (normally animated) menu will just be a black screen with no sound (the cursor might or might not be highlighted), but I have been able to launch the video by pressing enter.

And on a very rare occasion, I've just been able to play the video... which says to me that I don't actually have a problem with ubuntu itself, but with myth.

Any suggestions?

---

### Post by Wes Baker on 2010-10-02
Hi Mike,

Did you find a resolution to your problem?

I am having similar issues.  The errors seems to vary depending on which DVD I use to test.  Most notably, I am getting the following error in mythfrontend.log 100's of times per second while it tries to play some dvd's - and the screen just goes black until you hit the 'back' button (esc) on the remote.  

2010-10-02 22:19:04.614 AFD Error: Unknown decoding error
2010-10-02 22:19:04.614 [mpeg2video @ 0x57fb960]get_buffer() failed (stride changed)
2010-10-02 22:19:04.614 [mpeg2video @ 0x57fb960]get_buffer() failed (stride changed)

Meanwhile other dvd's seem to play ok, but it just skipd right past the menus!

Cheers,

Wes

---

### Post by &lt;mike&gt; on 2010-10-02
Hi Wes,

Sort of, yes. I updated my mythtv to the latest released version - 0.23.1 + fixes. Now I'm back to where I was in Karmic, where most (though not all) dvds play through the internal player.

In order to upgrade mythtv, you need either to install from source at [http://www.mythtv.org/](http://www.mythtv.org/) (which can be difficult) or change your source to use the mythbuntu nightly builds (instructions available at [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)).

There are downsides to this process... for me, the major one is that because the source is not hosted on my isp's ftp server, it's no longer unmetered and is slightly slower to update; and you don't automatically get pushed up to the latest version when a new one is released (you need to dpkg --reconfigure the mythbuntu-repos package to do it manually). But being able to watch my dvds without relying on an external player makes it worthwhile.

For the remaining dvds, I use vlc as a 'unique player command' (in the video screen, press I > metadata > edit metadata)

cvlc  --no-video-deco --no-fullscreen --no-osd --play-and-exit --key-play-pause Ctrl-P --key-quit Esc dvd://%s

if you don't use the whole of your screen for playback, you can specify the hight, width, and x and y offset using (the numbers here are examples)

--width 996 --height 700 --video-x 2 --video-y 29 

Mike

---

### Post by Wes Baker on 2010-10-04
Thanks Mike

The nightly builds (for 0.23.1) fixed the problems for me :)

Much appreciated!

---

