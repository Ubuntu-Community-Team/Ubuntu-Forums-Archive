---
title: "i have a problem with mplayer of lucid and libfribidi-dev"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-17
it seem to be that the current version of mplayer in the repositories(1.0~rc3+svn20090426-1ubuntu16)don't install libfribidi-dev package and is not configure with libfribidi-dev so installing it doesn't help

my problem is that hebrew translation in software like smplayer are reverse and as such unusable. 

i have compiled a new mplayer version from svn after installing libfribidi-dev so the problems is solved with gnome-mplayer and perhaps other mplayers clinets but not with smplayer.

the problem with smplayer is that i can't get it to use the compiled svn mplayer if i try
to change the path to the compiled mplayer version videos simply don't open in smplayer.

i compiled a new smplayer version to svn 3500 version but still i changing the path to the
compiled mplayer version in the new smplayer version doesn't work videos still don't work 
so what more can i do now?

is there a way to reconfigure lucid mplayer version 1.0~rc3+svn20090426-1ubuntu16 and enable libfribidi-dev or just for a new deb be released for lucid?

thanks in advance and i'm hopping that i explained my problem in a way that everyone would understand:lolflag:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679)

---

### Post by aviramof on 2010-04-17
any one?
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679)

---

### Post by mc4man on 2010-04-17
> that i explained my problem in a way that ..
Actually a little unsure of what your issue is.

Does smplayer not work at all or just not display the subs correctly?

Did you install your new mplayer build, and if so how?

If you start smplayer on a video and ck. the mplayer log what does it show? (Ctrl+m with focus on smplayer

---

### Post by rvm4000 on 2010-04-17
> **aviramof said:**
> i compiled a new smplayer version to svn 3500 version but still i changing the path to the
compiled mplayer version in the new smplayer version doesn't work videos still don't work 
so what more can i do now?

Copy the mplayer log after trying to play a file (options -> view logs). That would be very useful to know where the problem is.

---

### Post by aviramof on 2010-04-17
it did not display the subs correctly for instance the word correctly he show it like this "yltcerroc" and this is how all the translation look like and yes i installed my mplayer build.

i installed it by using ./configure ./configure --enable gui make sudo make install and when i write mplayer in terminal i see the svn version and as i said it's now works with gnome-mplayer.

but smplaye don't want to use the svn mplayer it insist of using this very old svn r1 that come with lucid that don't use libfribidi-dev and there for don't display it correctly amd 
if i try to change the path in smplayer it simply don't run videos.

---

### Post by rvm4000 on 2010-04-17
Does smplayer display any error? If it does, copy it here.

---

### Post by aviramof on 2010-04-17
no it does not as you can see in the pictures here:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/565679)

i tried all the options in the software and more and no luck so far the problem is the old 

mplayer that lucid use i think even karmic have a newer version and that is the cause of 

the problem that and the fact that smplayer want except the svn mplayer by not activating 

movies at all with it.

---

### Post by psyke83 on 2010-04-17
I think that you would need to install the "libfribidi0" package (-dev package are only the development sources, and usually don't include any compiled libraries).

Of course, mplayer may still not have been built with proper Hebrew support (so installing libfribidi0 may not have any effect), but you should try to install it anyway.

---

### Post by rvm4000 on 2010-04-17
I think you have two mplayers installed, one from a deb package (in /usr/bin) and another one compiled by yourself (probably installed in /usr/local/bin).

You need to tell smplayer which one to use. Go to preferences -> general and replace the mplayer executable to */usr/local/bin/mplayer*.

Then try to play a video. If it doesn't work, copy here any error message that smplayer may display, or the mplayer log (options -> view logs) if it doesn't display any error.

---

### Post by aviramof on 2010-04-18
as i said i have tried to tell smplayer to use [I]/usr/local/bin/mplayer but when i do that it stop opening videos at all all i get is a messege at the bottom of the screen subtitles on and that it nothing happen.

as for [/I]libfribidi0 it seem to be that i already have it installed maybe i installed it with mplayer or smplayer any way it doesn't do much to fix the problem.

---

### Post by rvm4000 on 2010-04-18
> **aviramof said:**
> as i said i have tried to tell smplayer to use [I]/usr/local/bin/mplayer but when i do that it stop opening videos at all all i get is a messege at the bottom of the screen subtitles on and that it nothing happen.

Could you please copy the mplayer log (options -> view logs) when that happens?

I can't help you without that information...

---

### Post by aviramof on 2010-04-18
Here you go mplayer logs when i use svn r1 that lucid have in it repositories :
```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/local/share/smplayer/input.conf -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/ofir/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:he:ISO-8859-8 -vid 0 -aid 1 -subpos 100 -cache 2000 -ss 786 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
  bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 bt_audio_service_open: connect() failed: Connection refused (111)
 MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
  Playing /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi.
  Cache fill:  0.00% (0 bytes)   
 AVI file format detected.
 ID_VIDEO_ID=0
 [aviheader] Video stream found, -vid 0
 ID_AUDIO_ID=1
 [aviheader] Audio stream found, -aid 1
 AVI: ODML: Building ODML index (2 superindexchunks).
 VIDEO:  [XVID]  720x400  24bpp  23.976 fps  1475.5 kbps (180.1 kbyte/s)
 Clip info:
  Software: VirtualDubMod 1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_NAME0=Software
 ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_N=1
 SUB: Detected subtitle file format: subviewer
 ENCA detection failed: fallback to ISO-8859-8
 SUB: Read 1570 subtitles.
 SUB: Adjusted 2 subtitle(s).
 ENCA detection failed: fallback to ISO-8859-8
 ENCA detection failed: fallback to ISO-8859-8
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 SUB: Added subtitle file (1): /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 ID_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
 ID_DEMUXER=avi
 ID_VIDEO_FORMAT=XVID
 ID_VIDEO_BITRATE=1475456
 ID_VIDEO_WIDTH=720
 ID_VIDEO_HEIGHT=400
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=9702.03
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 [***] auto-open
 Opening video filter: [screenshot]
 [***] Init
 [***] Updating font cache.
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
 ==========================================================================
 ID_VIDEO_CODEC=ffodivx
 ==========================================================================
 Opening audio decoder: [liba52] AC3 decoding with liba52
 Using SSE optimized IMDCT transform
 Using MMX optimized resampler
 AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [a52] afm: liba52 (AC3-liba52)
 ==========================================================================
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=a52
 Starting playback...
 [mpeg4 @ 0x5b52ac0]Invalid and inefficient vfw-avi packed B frames detected
 VDec: vo config request - 720 x 400 (preferred colorspace: Planar YV12)
 VDec: using Planar YV12 as output csp (no 0)
 Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=1.8000
 [swscaler @ 0x902900]No accelerated colorspace conversion found.
 [swscaler @ 0x902900]using unscaled yuv420p -> rgb24 special converter
 VO: [xv] 720x400 => 720x400 Planar YV12 
 [***] PlayResX undefined, setting 518.
 [Mixer] No hardware mixing, inserting volume filter.
  Exiting... (Quit)
 ID_EXIT=QUIT
 

```Smplayer logs:
```
  p, li { white-space: pre-wrap; }  [16:37:37:671] main: lock_file: /home/ofir/.config/smplayer/smplayer_init.lock
 [16:37:37:671] global_init
 [16:37:37:671] global_init: config file: '/home/ofir/.config/smplayer/smplayer.ini'
 [16:37:37:672] Preferences::load
 [16:37:37:672] AssStyles::load
 [16:37:37:673] Translator::loadCatalog: can't load qt_he_IL from /usr/local/share/smplayer/translations
 [16:37:37:673] Translator::loadCatalog: can't load qt_he_IL from /usr/share/qt4/translations
 [16:37:37:674] Translator::loadCatalog: can't load smplayer_he_IL from /usr/local/share/smplayer/translations
 [16:37:37:674] This is SMPlayer v. 0.6.9+SVN-r3500 running on Linux
 [16:37:37:674] Compiled with Qt v. 4.6.2, using 4.6.2
 [16:37:37:674]  * application path: '/usr/local/bin'
 [16:37:37:674]  * data path: '/usr/local/share/smplayer'
 [16:37:37:674]  * translation path: '/usr/local/share/smplayer/translations'
 [16:37:37:674]  * doc path: '/usr/local/share/doc/packages/smplayer'
 [16:37:37:674]  * themes path: '/usr/local/share/smplayer/themes'
 [16:37:37:674]  * shortcuts path: '/usr/local/share/smplayer/shortcuts'
 [16:37:37:674]  * config path: '/home/ofir/.config/smplayer'
 [16:37:37:674]  * ini path: '/home/ofir/.config/smplayer'
 [16:37:37:674]  * file for subtitles' styles: '/home/ofir/.config/smplayer/styles.***'
 [16:37:37:674]  * current path: '/home/ofir'
 [16:37:37:674] SMPlayer::processArgs: arguments: 1
 [16:37:37:675] SMPlayer::processArgs: 0 = smplayer
 [16:37:37:675] SMPlayer::processArgs: files_to_play: count: 0
 [16:37:37:675] MyClient::MyClient
 [16:37:37:675] SMPlayer::processArgs: trying to connect to port 53425
 [16:37:37:675] SMPlayer::gui: changed working directory to app path
 [16:37:37:675] SMPlayer::gui: current directory: /usr/local/bin
 [16:37:37:676] Screen::setAutoHideCursor: 0
 [16:37:37:676] Screen::setAutoHideCursor: 0
 [16:37:37:686] Core::changeFileSettingsMethod: hash
 [16:37:37:686] MplayerLayer::setRepaintBackground: 0
 [16:37:37:686] Preferences::monitor_aspect_double
 [16:37:37:686]  warning: monitor_aspect couldn't be parsed!
 [16:37:37:686]  monitor_aspect set to 0
 [16:37:37:726] Playlist::setModified: 0
 [16:37:37:734] Playlist::loadSettings
 [16:37:37:734] Playlist::addItem: '/home/ofir/&#1492;&#1493;&#1512;&#1491;&#1493;&#1514;/Legend.of.the.Seeker.S02E17.720p.HDTV.X264-DIMENSION/Legend.of.the.Seeker.S02E17.720p.HDTV.X264-DIMENSION.mkv'
 [16:37:37:734] Playlist::setModified: 0
 [16:37:37:734] Playlist::updateView
 [16:37:37:736] Playlist::updateView: name: 'Legend.of.the.Seeker.S02E17.720p.HDTV.X264-DIMENSION.mkv'
 [16:37:37:745] Style name: 'gtk+'
 [16:37:37:745] Style class name: 'QGtkStyle'
 [16:37:37:829] Favorites::load
 [16:37:37:830] TVList::parse_channels_conf
 [16:37:37:830] VList::parse_channels_conf: /home/ofir/.mplayer/channels.conf.ter doesn't exist
 [16:37:37:830] TVList::parse_channels_conf: can't open /home/ofir/.mplayer/channels.conf
 [16:37:37:830] Favorites::load
 [16:37:37:830] TVList::parse_channels_conf
 [16:37:37:830] VList::parse_channels_conf: /home/ofir/.mplayer/channels.conf.ter doesn't exist
 [16:37:37:831] TVList::parse_channels_conf: can't open /home/ofir/.mplayer/channels.conf
 [16:37:37:835] BaseGui::initializeMenus
 [16:37:37:873] BaseGui::initializeMenus
 [16:37:37:873] BaseGui::updateRecents
 [16:37:37:874] BaseGui::updateWidgets
 [16:37:37:874] Core::changeUseAss: 1
 [16:37:37:874] Core::changeSubVisilibity: 1
 [16:37:37:874] Core::tellmp: 'sub_visibility 1'
 [16:37:37:874] WARNING:  tellmp: no process running: sub_visibility 1
 [16:37:37:874] Core::displayMessage
 [16:37:37:875] BaseGui::setStayOnTop: 0
 [16:37:37:875] BaseGui::setStayOnTop: nothing to do
 [16:37:37:875] BaseGui::updateWidgets
 [16:37:37:875] BaseGui::updateRecents
 [16:37:37:875] Preferences::save
 [16:37:37:876] AssStyles::save
 [16:37:37:880] BaseGui::initializeGui: server running on port 50543
 [16:37:37:902] BaseGui::initializeMenus
 [16:37:37:902] BaseGui::updateRecents
 [16:37:37:902] BaseGui::updateWidgets
 [16:37:37:903] BaseGuiPlus::loadConfig
 [16:37:37:903] DefaultGui::createStatusBar
 [16:37:37:905] DefaultGui::createActions
 [16:37:37:906] DefaultGui::createControlWidget
 [16:37:37:906] DefaultGui::createControlWidgetMini
 [16:37:37:926] BaseGui::initializeMenus
 [16:37:37:926] BaseGui::updateRecents
 [16:37:37:927] DefaultGui::updateWidgets
 [16:37:37:927] BaseGui::updateWidgets
 [16:37:37:930] DefaultGui::loadConfig
 [16:37:37:930] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:1024
 [16:37:37:930] ToolbarEditor::load: 'toolbar1'
 [16:37:37:930] ToolbarEditor::load: loading action open_file
 [16:37:37:930] ToolbarEditor::load: loading action open_dvd
 [16:37:37:930] ToolbarEditor::load: loading action open_url
 [16:37:37:931] ToolbarEditor::load: loading action separator
 [16:37:37:931] ToolbarEditor::load: adding separator
 [16:37:37:931] ToolbarEditor::load: loading action compact
 [16:37:37:931] ToolbarEditor::load: loading action fullscreen
 [16:37:37:931] ToolbarEditor::load: loading action separator
 [16:37:37:931] ToolbarEditor::load: adding separator
 [16:37:37:931] ToolbarEditor::load: loading action screenshot
 [16:37:37:931] ToolbarEditor::load: loading action separator
 [16:37:37:931] ToolbarEditor::load: adding separator
 [16:37:37:931] ToolbarEditor::load: loading action show_file_properties
 [16:37:37:931] ToolbarEditor::load: loading action show_playlist
 [16:37:37:931] ToolbarEditor::load: loading action show_preferences
 [16:37:37:932] ToolbarEditor::load: loading action separator
 [16:37:37:932] ToolbarEditor::load: adding separator
 [16:37:37:932] ToolbarEditor::load: loading action play_prev
 [16:37:37:932] ToolbarEditor::load: loading action play_next
 [16:37:37:932] ToolbarEditor::load: 'controlwidget'
 [16:37:37:932] ToolbarEditor::load: loading action play
 [16:37:37:932] ToolbarEditor::load: loading action pause_and_frame_step
 [16:37:37:932] ToolbarEditor::load: loading action stop
 [16:37:37:932] ToolbarEditor::load: loading action separator
 [16:37:37:932] ToolbarEditor::load: adding separator
 [16:37:37:932] ToolbarEditor::load: loading action rewindbutton_action
 [16:37:37:933] ToolbarEditor::load: loading action timeslider_action
 [16:37:37:933] TimeSlider::setDragDelay: 100
 [16:37:37:933] ToolbarEditor::load: loading action forwardbutton_action
 [16:37:37:933] ToolbarEditor::load: loading action separator
 [16:37:37:933] ToolbarEditor::load: adding separator
 [16:37:37:933] ToolbarEditor::load: loading action fullscreen
 [16:37:37:933] ToolbarEditor::load: loading action mute
 [16:37:37:933] ToolbarEditor::load: loading action volumeslider_action
 [16:37:37:933] ToolbarEditor::load: 'controlwidget_mini'
 [16:37:37:934] ToolbarEditor::load: loading action play_or_pause
 [16:37:37:934] ToolbarEditor::load: loading action stop
 [16:37:37:934] ToolbarEditor::load: loading action separator
 [16:37:37:934] ToolbarEditor::load: adding separator
 [16:37:37:934] ToolbarEditor::load: loading action rewind1
 [16:37:37:934] ToolbarEditor::load: loading action timeslider_action
 [16:37:37:934] TimeSlider::setDragDelay: 100
 [16:37:37:934] ToolbarEditor::load: loading action forward1
 [16:37:37:934] ToolbarEditor::load: loading action separator
 [16:37:37:934] ToolbarEditor::load: adding separator
 [16:37:37:935] ToolbarEditor::load: loading action mute
 [16:37:37:935] ToolbarEditor::load: loading action volumeslider_action
 [16:37:37:935] ToolbarEditor::load: ''
 [16:37:37:935] ToolbarEditor::load: loading action play
 [16:37:37:935] ToolbarEditor::load: loading action pause
 [16:37:37:936] ToolbarEditor::load: loading action stop
 [16:37:37:936] ToolbarEditor::load: loading action separator
 [16:37:37:936] ToolbarEditor::load: adding separator
 [16:37:37:936] ToolbarEditor::load: loading action rewindbutton_action
 [16:37:37:936] ToolbarEditor::load: loading action timeslider_action
 [16:37:37:936] TimeSlider::setDragDelay: 100
 [16:37:37:936] ToolbarEditor::load: loading action forwardbutton_action
 [16:37:37:937] ToolbarEditor::load: loading action separator
 [16:37:37:937] ToolbarEditor::load: adding separator
 [16:37:37:937] ToolbarEditor::load: loading action fullscreen
 [16:37:37:937] ToolbarEditor::load: loading action mute
 [16:37:37:937] ToolbarEditor::load: loading action volumeslider_action
 [16:37:37:937] ToolbarEditor::load: loading action separator
 [16:37:37:937] ToolbarEditor::load: adding separator
 [16:37:37:937] ToolbarEditor::load: loading action timelabel_action
 [16:37:37:938] Helper::qtVersion: 4602
 [16:37:37:940] DefaultGui::loadConfig: playlist visible: 0
 [16:37:37:940] DefaultGui::loadConfig: playlist position: 0, 0
 [16:37:37:940] DefaultGui::loadConfig: playlist size: 100 x 30
 [16:37:37:940] DefaultGui::updateWidgets
 [16:37:37:941] BaseGui::updateWidgets
 [16:37:37:948] BaseGui::showEvent
 [16:37:37:949] main: remove_lock: /home/ofir/.config/smplayer/smplayer_init.lock
 [16:37:37:953] BaseGui::loadActions
 [16:37:37:953] ActionsEditor::loadFromConfig
 [16:37:38:072] BaseGui::initializeMenus
 [16:37:38:072] BaseGui::updateRecents
 [16:37:38:073] DefaultGui::updateWidgets
 [16:37:38:073] BaseGui::updateWidgets
 [16:37:49:408] BaseGui::showMplayerLog
 [16:37:52:856] BaseGui::fileOpen
 [16:37:58:248] BaseGui::openFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:248] Core::openFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:248] Core::playNewFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:248] Core::saveMediaInfo
 [16:37:58:248] FileSettingsHash::existSettingsFor: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:298] FileSettingsHash::existSettingsFor: config_file: '/home/ofir/.config/smplayer/file_settings/f/f0ed5a78080a4ade.ini'
 [16:37:58:308] Core::playNewFile: We have settings for this file!!!
 [16:37:58:309] FileSettings::loadSettingsFor: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:311] FileSettingsHash::loadSettingsFor: config_file: '/home/ofir/.config/smplayer/file_settings/f/f0ed5a78080a4ade.ini'
 [16:37:58:322] MediaSettings::load
 [16:37:58:323] Core::playNewFile: Media settings read
 [16:37:58:323] BaseGuiPlus::resizeWindow: 720, 400
 [16:37:58:323] BaseGui::resizeWindow: 720, 400
 [16:37:58:323] BaseGui::resizeWindow: size to scale: 720, 400
 [16:37:58:324] BaseGui::resizeWindow: done: window size: 720, 529
 [16:37:58:324] BaseGui::resizeWindow: done: panel->size: 720, 400
 [16:37:58:325] BaseGui::resizeWindow: done: mplayerwindow->size: 720, 400
 [16:37:58:325] Core::changeAspectRatio: 1
 [16:37:58:325] Core::displayMessage
 [16:37:58:398] Core::playNewFile: volume: 40, old_volume: 40
 [16:37:58:399] Core::initPlaying
 [16:37:58:399] Core::startMplayer
 [16:37:58:399] Core::startMplayer: setting working directory to '/home/ofir/.config/smplayer/screenshots'
 [16:37:58:399] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:37:58:399] MplayerVersion::isMplayerAtLeast: comparing 27667 with 1
 [16:37:58:399] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:37:58:399] MplayerVersion::isMplayerAtLeast: comparing 29058 with 1
 [16:37:58:399] Core::startMplayer: * not using -colorkey for xv
 [16:37:58:399] Core::startMplayer: * report if you can't see the video
 [16:37:58:399] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:37:58:400] MplayerVersion::isMplayerAtLeast: comparing 27872 with 1
 [16:37:58:400] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:37:58:400] MplayerVersion::isMplayerAtLeast: comparing 24924 with 1
 [16:37:58:400] Core::startMplayer: file basename: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON'
 [16:37:58:400] Core::startMplayer: edl file: ''
 [16:37:58:400] MplayerLayer::playingStarted
 [16:37:58:401] Screen::playingStarted
 [16:37:58:401] Screen::setAutoHideCursor: 1
 [16:37:58:401] Screen::playingStarted
 [16:37:58:401] Screen::setAutoHideCursor: 1
 [16:37:58:401] Core::startMplayer: command: '/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/local/share/smplayer/input.conf -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/ofir/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:he:ISO-8859-8 -vid 0 -aid 1 -subpos 100 -cache 2000 -ss 786 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:405] Playlist::setModified: 0
 [16:37:58:405] Playlist::addFiles
 [16:37:58:405] Playlist::addItem: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:406] Playlist::updateView
 [16:37:58:406] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:37:58:407] Playlist::addFiles: latest_dir: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON'
 [16:37:59:070] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:077] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:077] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:078] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:138] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:140] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:140] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:141] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:205] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:206] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:207] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:208] MplayerProcess::parseLine: 'bt_audio_service_open: connect() failed: Connection refused (111)'
 [16:37:59:266] MplayerProcess::parseLine: 'MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team'
 [16:37:59:267] MplayerVersion::mplayerVersion: MPlayer SVN revision found: 1
 [16:37:59:267] MplayerProcess::parseLine: MPlayer SVN: 1
 [16:37:59:290] MplayerProcess::parseLine: 'mplayer: could not connect to socket'
 [16:37:59:290] MplayerProcess::parseLine: 'mplayer: No such file or directory'
 [16:37:59:291] MplayerProcess::parseLine: 'Failed to open LIRC support. You will not be able to use your remote control.'
 [16:37:59:291] MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
 [16:37:59:291] MplayerProcess::parseLine: ''
 [16:37:59:291] MplayerProcess::parseLine: 'Playing /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi.'
 [16:37:59:292] MplayerProcess::parseLine: ''
 [16:37:59:493] MplayerProcess::parseLine: 'Cache fill:  0.00% (0 bytes)   '
 [16:37:59:493] Core::displayMessage
 [16:37:59:494] MplayerProcess::parseLine: 'AVI file format detected.'
 [16:37:59:505] MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
 [16:37:59:505] MplayerProcess::parseLine: ID_VIDEO_ID: 0
 [16:37:59:505] MplayerProcess::parseLine: '[aviheader] Video stream found, -vid 0'
 [16:37:59:505] MplayerProcess::parseLine: 'ID_AUDIO_ID=1'
 [16:37:59:505] MplayerProcess::parseLine: ID_AUDIO_ID: 1
 [16:37:59:505] MplayerProcess::parseLine: '[aviheader] Audio stream found, -aid 1'
 [16:37:59:721] MplayerProcess::parseLine: 'AVI: ODML: Building ODML index (2 superindexchunks).'
 [16:38:00:213] MplayerProcess::parseLine: 'VIDEO:  [XVID]  720x400  24bpp  23.976 fps  1475.5 kbps (180.1 kbyte/s)'
 [16:38:00:214] MplayerProcess::parseLine: 'Clip info:'
 [16:38:00:214] MplayerProcess::parseLine: ' Software: VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:38:00:214] MplayerProcess::parseLine: clip_software: 'VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:38:00:215] MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME0=Software'
 [16:38:00:215] MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:38:00:215] MplayerProcess::parseLine: 'ID_CLIP_INFO_N=1'
 [16:38:00:230] MplayerProcess::parseLine: 'SUB: Detected subtitle file format: subviewer'
 [16:38:00:247] MplayerProcess::parseLine: 'ENCA detection failed: fallback to ISO-8859-8'
 [16:38:00:284] MplayerProcess::parseLine: 'SUB: Read 1570 subtitles.'
 [16:38:00:284] MplayerProcess::parseLine: 'SUB: Adjusted 2 subtitle(s).'
 [16:38:00:299] MplayerProcess::parseLine: 'ENCA detection failed: fallback to ISO-8859-8'
 [16:38:00:311] MplayerProcess::parseLine: 'ENCA detection failed: fallback to ISO-8859-8'
 [16:38:00:316] MplayerProcess::parseLine: 'ID_FILE_SUB_ID=0'
 [16:38:00:316] SubTracks::parse: 'ID_FILE_SUB_ID=0'
 [16:38:00:317] SubTracks::find: item type: 2, ID: 0 doesn't exist
 [16:38:00:317] MplayerProcess::parseLine: 'ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:38:00:317] SubTracks::parse: 'ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:38:00:318] MplayerProcess::parseLine: 'SUB: Added subtitle file (1): /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:38:00:318] MplayerProcess::parseLine: 'ID_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:38:00:318] MplayerProcess::parseLine: 'ID_DEMUXER=avi'
 [16:38:00:318] MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=XVID'
 [16:38:00:318] MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=1475456'
 [16:38:00:318] MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=720'
 [16:38:00:319] MplayerProcess::parseLine: md.video_width set to 720
 [16:38:00:319] MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=400'
 [16:38:00:319] MplayerProcess::parseLine: md.video_height set to 400
 [16:38:00:319] MplayerProcess::parseLine: 'ID_VIDEO_FPS=23.976'
 [16:38:00:319] MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=0.0000'
 [16:38:00:319] MplayerProcess::parseLine: md.video_aspect set to 1.800000
 [16:38:00:319] MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=8192'
 [16:38:00:319] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=448000'
 [16:38:00:319] MplayerProcess::parseLine: 'ID_AUDIO_RATE=0'
 [16:38:00:319] MplayerProcess::parseLine: 'ID_AUDIO_NCH=0'
 [16:38:00:320] MplayerProcess::parseLine: 'ID_LENGTH=9702.03'
 [16:38:00:320] MplayerProcess::parseLine: md.duration set to 9702.030000
 [16:38:00:320] MplayerProcess::parseLine: 'ID_SEEKABLE=1'
 [16:38:00:352] MplayerProcess::parseLine: 'ID_CHAPTERS=0'
 [16:38:00:402] MplayerProcess::parseLine: '[***] auto-open'
 [16:38:00:402] MplayerProcess::parseLine: 'Opening video filter: [screenshot]'
 [16:38:00:404] MplayerProcess::parseLine: '[***] Init'
 [16:38:00:404] Core::displayUpdatingFontCache
 [16:38:00:412] MplayerProcess::parseLine: '[***] Updating font cache.'
 [16:38:00:412] Core::displayUpdatingFontCache
 [16:38:00:412] MplayerProcess::parseLine: '=========================================================================='
 [16:38:00:413] MplayerProcess::parseLine: 'Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family'
 [16:38:00:416] MplayerProcess::parseLine: 'Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)'
 [16:38:00:416] MplayerProcess::parseLine: '=========================================================================='
 [16:38:00:416] MplayerProcess::parseLine: 'ID_VIDEO_CODEC=ffodivx'
 [16:38:00:416] MplayerProcess::parseLine: '=========================================================================='
 [16:38:00:417] MplayerProcess::parseLine: 'Opening audio decoder: [liba52] AC3 decoding with liba52'
 [16:38:00:418] MplayerProcess::parseLine: 'Using SSE optimized IMDCT transform'
 [16:38:00:418] MplayerProcess::parseLine: 'Using MMX optimized resampler'
 [16:38:00:418] MplayerProcess::parseLine: 'AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)'
 [16:38:00:418] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=448000'
 [16:38:00:418] MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
 [16:38:00:418] MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
 [16:38:00:418] MplayerProcess::parseLine: 'Selected audio codec: [a52] afm: liba52 (AC3-liba52)'
 [16:38:00:419] MplayerProcess::parseLine: '=========================================================================='
 [16:38:00:426] MplayerProcess::parseLine: 'AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)'
 [16:38:00:426] Core::gotAO: 'pulse'
 [16:38:00:426] MplayerProcess::parseLine: 'ID_AUDIO_CODEC=a52'
 [16:38:00:427] MplayerProcess::parseLine: 'Starting playback...'
 [16:38:00:533] MplayerProcess::parseLine: '[mpeg4 @ 0x5b52ac0]Invalid and inefficient vfw-avi packed B frames detected'
 [16:38:00:535] MplayerProcess::parseLine: 'VDec: vo config request - 720 x 400 (preferred colorspace: Planar YV12)'
 [16:38:00:535] MplayerProcess::parseLine: 'VDec: using Planar YV12 as output csp (no 0)'
 [16:38:00:536] MplayerProcess::parseLine: 'Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.'
 [16:38:00:536] MplayerProcess::parseLine: md.video_aspect set to 1.800000
 [16:38:00:536] MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.8000'
 [16:38:00:536] MplayerProcess::parseLine: md.video_aspect set to 1.800000
 [16:38:00:536] MplayerProcess::parseLine: '[swscaler @ 0x902900]No accelerated colorspace conversion found.'
 [16:38:00:536] MplayerProcess::parseLine: '[swscaler @ 0x902900]using unscaled yuv420p -> rgb24 special converter'
 [16:38:00:538] MplayerProcess::parseLine: 'VO: [xv] 720x400 => 720x400 Planar YV12 '
 [16:38:00:538] Core::gotVO: 'xv'
 [16:38:00:538] Core::gotWindowResolution: 720, 400
 [16:38:00:538] BaseGuiPlus::resizeWindow: 720, 400
 [16:38:00:538] BaseGui::resizeWindow: 720, 400
 [16:38:00:538] BaseGui::resizeWindow: size to scale: 720, 400
 [16:38:00:538] BaseGui::resizeWindow: the panel size is already the required size. Doing nothing.
 [16:38:00:552] MplayerProcess::parseLine: starting sec: 796.800000
 [16:38:00:552] Core::gotStartingTime: 796.800000
 [16:38:00:553] Core::gotStartingTime: current_sec: 786.600000
 [16:38:00:553] BaseGui::displayState: Playing
 [16:38:00:566] BaseGui::togglePlayAction
 [16:38:00:566] Core::changeCurrentSec: mplayer reports that now it's playing
 [16:38:00:569] Core::finishRestart: --- start ---
 [16:38:00:569] Core::newMediaPlaying: --- start ---
 [16:38:00:569] Core::initializeMenus
 [16:38:00:569] BaseGui::initializeMenus
 [16:38:00:570] MediaData::list
 [16:38:00:570]   filename: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:38:00:570]   duration: 9702.030000
 [16:38:00:570]   video_width: 720
 [16:38:00:570]   video_height: 400
 [16:38:00:570]   video_aspect: 1.800000
 [16:38:00:570]   type: 0
 [16:38:00:570]   novideo: 0
 [16:38:00:570]   dvd_id: ''
 [16:38:00:570]   initialized: 1
 [16:38:00:570]   chapters: 0
 [16:38:00:570]   Subs:
 [16:38:00:570]   Programs:
 [16:38:00:570]   Videos:
 [16:38:00:570] Tracks::list: item 0: ID: 0 lang: '' name: ''
 [16:38:00:570]   Audios:
 [16:38:00:570]   Titles:
 [16:38:00:570]   demuxer: 'avi'
 [16:38:00:571]   video_format: 'XVID'
 [16:38:00:571]   audio_format: '8192'
 [16:38:00:571]   video_bitrate: 1475456
 [16:38:00:571]   video_fps: '23.976'
 [16:38:00:571]   audio_bitrate: 448000
 [16:38:00:571]   audio_rate: 48000
 [16:38:00:571]   audio_nch: 2
 [16:38:00:571]   video_codec: 'ffodivx'
 [16:38:00:571]   audio_codec: 'a52'
 [16:38:00:571] MediaSettings::list
 [16:38:00:571]   current_sec: 796.500000
 [16:38:00:571]   current_sub_id: 0
 [16:38:00:571]   current_program_id: -1000
 [16:38:00:571]   current_video_id: 0
 [16:38:00:571]   current_audio_id: 1
 [16:38:00:571]   current_title_id: -1000
 [16:38:00:571]   current_chapter_id: 0
 [16:38:00:571]   current_angle_id: -1000
 [16:38:00:571]   aspect_ratio_id: 1
 [16:38:00:571]   volume: 40
 [16:38:00:572]   mute: 0
 [16:38:00:572]   external_subtitles: ''
 [16:38:00:572]   external_audio: ''
 [16:38:00:572]   sub_delay: 0
 [16:38:00:572]   audio_delay: 0
 [16:38:00:572]   sub_pos: 100
 [16:38:00:572]   sub_scale: 5.000000
 [16:38:00:572]   sub_scale_***: 1.000000
 [16:38:00:572]   brightness: 0
 [16:38:00:572]   contrast: 0
 [16:38:00:572]   gamma: 0
 [16:38:00:572]   hue: 0
 [16:38:00:572]   saturation: 0
 [16:38:00:572]   speed: 1.000000
 [16:38:00:572]   phase_filter: 0
 [16:38:00:572]   current_denoiser: 0
 [16:38:00:572]   deblock_filter: 0
 [16:38:00:572]   dering_filter: 0
 [16:38:00:572]   noise_filter: 0
 [16:38:00:572]   postprocessing_filter: 0
 [16:38:00:573]   upscaling_filter: 0
 [16:38:00:573]   current_deinterlacer: 0
 [16:38:00:573]   add_letterbox: 0
 [16:38:00:573]   karaoke_filter: 0
 [16:38:00:573]   extrastereo_filter: 0
 [16:38:00:573]   volnorm_filter: 0
 [16:38:00:573]   audio_use_channels: 2
 [16:38:00:573]   stereo_mode: 0
 [16:38:00:573]   zoom_factor: 1.000000
 [16:38:00:573]   rotate: -1
 [16:38:00:573]   flip: 0
 [16:38:00:573]   mirror: 0
 [16:38:00:573]   loop: 0
 [16:38:00:573]   A_marker: -1
 [16:38:00:573]   B_marker: -1
 [16:38:00:573]   forced_demuxer: ''
 [16:38:00:573]   forced_video_codec: ''
 [16:38:00:573]   forced_audio_codec: ''
 [16:38:00:573]   original_demuxer: ''
 [16:38:00:573]   original_video_codec: ''
 [16:38:00:574]   original_audio_codec: ''
 [16:38:00:574]   mplayer_additional_options: ''
 [16:38:00:574]   mplayer_additional_video_filters: ''
 [16:38:00:574]   mplayer_additional_audio_filters: ''
 [16:38:00:574]   win_width: 720
 [16:38:00:574]   win_height: 400
 [16:38:00:574]   win_aspect(): 1.800000
 [16:38:00:574]   starting_time: 0.300000
 [16:38:00:574]   is264andHD: 0
 [16:38:00:574] Core::newMediaPlaying: --- end ---
 [16:38:00:574] BaseGui::enterFullscreenOnPlay: arg_start_in_fullscreen: -1, pref->start_in_fullscreen: 0
 [16:38:00:574] Core::changeAspectRatio: 1
 [16:38:00:574] Core::displayMessage
 [16:38:00:575] Core::setVolume: 100
 [16:38:00:575] Core::tellmp: 'volume 100 1'
 [16:38:00:575] Core::updateWidgets
 [16:38:00:575] DefaultGui::updateWidgets
 [16:38:00:576] BaseGui::updateWidgets
 [16:38:00:576] Core::displayMessage
 [16:38:00:576] Core::changeZoom: 1.000000
 [16:38:00:576] Core::displayMessage
 [16:38:00:580] Core::changeSubVisilibity: 1
 [16:38:00:580] Core::tellmp: 'sub_visibility 1'
 [16:38:00:580] Core::displayMessage
 [16:38:00:580] DefaultGui::enableActionsOnPlaying
 [16:38:00:580] BaseGui::enableActionsOnPlaying
 [16:38:00:581] BaseGui::autosaveMplayerLog
 [16:38:00:581] Playlist:: getMediaInfo
 [16:38:00:582] Playlist::updateView
 [16:38:00:582] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:38:00:582] BaseGuiPlus::updateMediaInfo
 [16:38:00:582] BaseGui::updateMediaInfo
 [16:38:00:583] Core::updateWidgets
 [16:38:00:583] DefaultGui::updateWidgets
 [16:38:00:583] BaseGui::updateWidgets
 [16:38:00:583] Core::finishRestart: --- end ---
 [16:38:00:583] BaseGui::checkStayOnTop
 [16:38:00:623] MplayerProcess::parseLine: '[***] PlayResX undefined, setting 518.'
 [16:38:00:623] MplayerProcess::parseLine: subtitle_info_changed
 [16:38:00:623] MplayerProcess::parseLine: audio_info_changed
 [16:38:00:623] BaseGui::newMediaLoaded
 [16:38:00:623] Recents::addItem: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:38:00:624] BaseGui::updateRecents
 [16:38:00:624] BaseGui::checkPendingActionsToRun
 [16:38:00:624] BaseGui::checkMplayerVersion
 [16:38:00:624] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:38:00:624] MplayerVersion::isMplayerAtLeast: comparing 25158 with 1
 [16:38:00:624] Core::checkIfVideoIsHD
 [16:38:00:625] Core::initSubtitleTrack
 [16:38:00:625] Core::initSubtitleTrack: num_items: 0
 [16:38:00:625] Core::initSubtitleTrack: previous subtitle: type: 1 id: -1
 [16:38:00:625] Core::initSubtitleTrack: list of subtitles:
 [16:38:00:625] SubTracks::list: item 0: type: 2 ID: 0 lang: '' name: '' filename: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:38:00:625] Core::initializeMenus
 [16:38:00:625] BaseGui::initializeMenus
 [16:38:00:626] Core::initSubtitleTrack: restoring subtitle
 [16:38:00:626] Core::changeSubtitle: 0
 [16:38:00:626] Core::changeSubtitle: ID: 0
 [16:38:00:626] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:38:00:626] MplayerVersion::isMplayerAtLeast: comparing 25158 with 1
 [16:38:00:626] Core::tellmp: 'sub_select 0'
 [16:38:00:626] Core::updateWidgets
 [16:38:00:626] DefaultGui::updateWidgets
 [16:38:00:626] BaseGui::updateWidgets
 [16:38:00:626] Core::updateWidgets
 [16:38:00:626] DefaultGui::updateWidgets
 [16:38:00:626] BaseGui::updateWidgets
 [16:38:00:627] Core::initAudioTrack
 [16:38:00:627] Core::initAudioTrack: num_items: 0
 [16:38:00:627] Core::initAudioTrack: list of audios:
 [16:38:00:627] Tracks::list: item 1: ID: 1 lang: '' name: ''
 [16:38:00:627] Core::initializeMenus
 [16:38:00:627] BaseGui::initializeMenus
 [16:38:00:627] Core::initAudioTrack: restoring audio
 [16:38:00:627] Core::updateWidgets
 [16:38:00:627] DefaultGui::updateWidgets
 [16:38:00:627] BaseGui::updateWidgets
 [16:38:00:627] DefaultGui::enableActionsOnPlaying
 [16:38:00:627] BaseGui::enableActionsOnPlaying
 [16:38:00:633] MplayerProcess::parseLine: '[Mixer] No hardware mixing, inserting volume filter.'
 [16:38:01:624] BaseGui::displayWarningAboutOldMplayer
 [16:38:02:663] Core::stop
 [16:38:02:663] Core::stop: state: Playing
 [16:38:02:663] Core::stopMplayer
 [16:38:02:664] Core::tellmp: 'quit'
 [16:38:02:664] Core::stopMplayer: Waiting mplayer to finish...
 [16:38:02:694] MplayerProcess::parseLine: ''
 [16:38:02:695] MplayerProcess::parseLine: 'Exiting... (Quit)'
 [16:38:02:695] MplayerProcess::parseLine: 'ID_EXIT=QUIT'
 [16:38:02:699] MyProcess::procFinished
 [16:38:02:699] MyProcess::procFinished: Bytes available: 0
 [16:38:02:699] MplayerProcess::processFinished: exitCode: 0, status: 0
 [16:38:02:699] MplayerLayer::playingStopped
 [16:38:02:699] Screen::playingStopped
 [16:38:02:700] Screen::setAutoHideCursor: 0
 [16:38:02:700] Screen::playingStopped
 [16:38:02:700] Screen::setAutoHideCursor: 0
 [16:38:02:700] Core::stopMplayer: Finished. (I hope)
 [16:38:02:700] DefaultGui::disableActionsOnStop
 [16:38:02:700] BaseGui::disableActionsOnStop
 [16:38:02:709] Core::processFinished
 [16:38:02:709] Core::processFinished: we_are_restarting: 0
 [16:38:02:709] Core::processFinished: play has finished!
 [16:38:02:709] BaseGui::displayState: Stopped
 [16:38:02:710] BaseGui::togglePlayAction
 [16:38:02:710] Core::processFinished: exit_code: 0
 [16:38:02:711] BaseGui::checkStayOnTop
 [16:38:02:780] Core::changeOSD: 1
 [16:38:02:780] Core::pausing_prefix
 [16:38:02:781] WARNING: MplayerVersion::isMplayerAtLeast: there's no parsed version nor user supplied version!
 [16:38:02:781] MplayerVersion::isMplayerAtLeast: comparing 27665 with 1
 [16:38:02:781] Core::tellmp: 'pausing_keep osd 1'
 [16:38:02:781] WARNING:  tellmp: no process running: pausing_keep osd 1
 [16:38:02:781] Core::updateWidgets
 [16:38:02:781] DefaultGui::updateWidgets
 [16:38:02:781] BaseGui::updateWidgets
 [16:38:07:944] BaseGui::showMplayerLog
 [16:38:53:295] BaseGui::showLog
 

```

---

### Post by aviramof on 2010-04-18
and here with mplayer svn r31044 when smplayer don't start movies at  all.

```
  p, li { white-space: pre-wrap; }  /usr/local/bin/mplayer  -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv  -ao pulse -nokeepaspect -framedrop -nodr -double -input  nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 65012055  -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0  -***-font-scale 1 -***-styles /home/ofir/.config/smplayer/styles.***  -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20  -subfont-text-scale 20 -subcp enca:he:ISO-8859-8 -vid 0 -aid 1 -subpos  100 -volume 100 -cache 2000 -ss 798 -osdlevel 0 -vf-add screenshot  -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0  -softvol -softvol-max 110 /media/&#1491;&#1497;&#1505;&#1511;  &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
  MPlayer SVN-r31044-4.4.3 (C)  2000-2010 MPlayer Team
  Playing /media/&#1491;&#1497;&#1505;&#1511;  &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi.
  Cache fill:  0.00% (0 bytes)    
 AVI file format detected.
 ID_VIDEO_ID=0
 [aviheader] Video stream  found, -vid 0
 ID_AUDIO_ID=1
 [aviheader] Audio stream  found, -aid 1
 AVI: ODML: Building ODML index  (2 superindexchunks).
 VIDEO:  [XVID]  720x400  24bpp   23.976 fps  1475.5 kbps (180.1 kbyte/s)
 Clip info:
  Software: VirtualDubMod  1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_NAME0=Software
 ID_CLIP_INFO_VALUE0=VirtualDubMod  1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_N=1
 SUB: error opening iconv  descriptor.
 [***] Error opening iconv  descriptor
 [***] Error recoding file
 [***] Error opening iconv  descriptor
 [***] Error recoding file
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511;   &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 SUB: Added subtitle file (1):  /media/&#1491;&#1497;&#1505;&#1511;  &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 ID_FILENAME=/media/&#1491;&#1497;&#1505;&#1511;  &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
 ID_DEMUXER=avi
 ID_VIDEO_FORMAT=XVID
 ID_VIDEO_BITRATE=1475456
 ID_VIDEO_WIDTH=720
 ID_VIDEO_HEIGHT=400
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=9702.03
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Error opening/initializing the  selected video_out (-vo) device.
 ==========================================================================
 Opening audio decoder:  [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le,  448.0 kbit/29.17% (ratio: 56000->192000)
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffac3]  afm: ffmpeg (FFmpeg AC-3)
 ==========================================================================
 No such audio driver 'pulse'
 Could not open/initialize  audio device -> no sound.
 Audio: no sound
 Video: no video
   Exiting... (End of file)
 ID_EXIT=EOF
 

```Smplayer:
```
  p, li { white-space: pre-wrap; }  [16:46:08:224] main: lock_file: /home/ofir/.config/smplayer/smplayer_init.lock
 [16:46:08:224] global_init
 [16:46:08:225] global_init: config file: '/home/ofir/.config/smplayer/smplayer.ini'
 [16:46:08:225] Preferences::load
 [16:46:08:226] AssStyles::load
 [16:46:08:227] Translator::loadCatalog: can't load qt_he_IL from /usr/local/share/smplayer/translations
 [16:46:08:227] Translator::loadCatalog: can't load qt_he_IL from /usr/share/qt4/translations
 [16:46:08:227] Translator::loadCatalog: can't load smplayer_he_IL from /usr/local/share/smplayer/translations
 [16:46:08:227] This is SMPlayer v. 0.6.9+SVN-r3500 running on Linux
 [16:46:08:228] Compiled with Qt v. 4.6.2, using 4.6.2
 [16:46:08:228]  * application path: '/usr/local/bin'
 [16:46:08:228]  * data path: '/usr/local/share/smplayer'
 [16:46:08:228]  * translation path: '/usr/local/share/smplayer/translations'
 [16:46:08:228]  * doc path: '/usr/local/share/doc/packages/smplayer'
 [16:46:08:228]  * themes path: '/usr/local/share/smplayer/themes'
 [16:46:08:228]  * shortcuts path: '/usr/local/share/smplayer/shortcuts'
 [16:46:08:228]  * config path: '/home/ofir/.config/smplayer'
 [16:46:08:228]  * ini path: '/home/ofir/.config/smplayer'
 [16:46:08:228]  * file for subtitles' styles: '/home/ofir/.config/smplayer/styles.***'
 [16:46:08:228]  * current path: '/home/ofir'
 [16:46:08:228] SMPlayer::processArgs: arguments: 1
 [16:46:08:228] SMPlayer::processArgs: 0 = smplayer
 [16:46:08:228] SMPlayer::processArgs: files_to_play: count: 0
 [16:46:08:228] MyClient::MyClient
 [16:46:08:228] SMPlayer::processArgs: trying to connect to port 50543
 [16:46:08:229] SMPlayer::gui: changed working directory to app path
 [16:46:08:229] SMPlayer::gui: current directory: /usr/local/bin
 [16:46:08:230] Screen::setAutoHideCursor: 0
 [16:46:08:230] Screen::setAutoHideCursor: 0
 [16:46:08:239] Core::changeFileSettingsMethod: hash
 [16:46:08:240] MplayerLayer::setRepaintBackground: 0
 [16:46:08:240] Preferences::monitor_aspect_double
 [16:46:08:240]  warning: monitor_aspect couldn't be parsed!
 [16:46:08:240]  monitor_aspect set to 0
 [16:46:08:281] Playlist::setModified: 0
 [16:46:08:289] Playlist::loadSettings
 [16:46:08:289] Playlist::addItem: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:08:289] Playlist::setModified: 0
 [16:46:08:290] Playlist::updateView
 [16:46:08:292] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:08:300] Style name: 'gtk+'
 [16:46:08:301] Style class name: 'QGtkStyle'
 [16:46:08:386] Favorites::load
 [16:46:08:386] TVList::parse_channels_conf
 [16:46:08:387] VList::parse_channels_conf: /home/ofir/.mplayer/channels.conf.ter doesn't exist
 [16:46:08:387] TVList::parse_channels_conf: can't open /home/ofir/.mplayer/channels.conf
 [16:46:08:387] Favorites::load
 [16:46:08:387] TVList::parse_channels_conf
 [16:46:08:387] VList::parse_channels_conf: /home/ofir/.mplayer/channels.conf.ter doesn't exist
 [16:46:08:387] TVList::parse_channels_conf: can't open /home/ofir/.mplayer/channels.conf
 [16:46:08:392] BaseGui::initializeMenus
 [16:46:08:431] BaseGui::initializeMenus
 [16:46:08:431] BaseGui::updateRecents
 [16:46:08:432] BaseGui::updateWidgets
 [16:46:08:432] Core::changeUseAss: 1
 [16:46:08:432] Core::changeSubVisilibity: 1
 [16:46:08:432] Core::tellmp: 'sub_visibility 1'
 [16:46:08:432] WARNING:  tellmp: no process running: sub_visibility 1
 [16:46:08:432] Core::displayMessage
 [16:46:08:432] BaseGui::setStayOnTop: 0
 [16:46:08:432] BaseGui::setStayOnTop: nothing to do
 [16:46:08:433] BaseGui::updateWidgets
 [16:46:08:433] BaseGui::updateRecents
 [16:46:08:433] Preferences::save
 [16:46:08:434] AssStyles::save
 [16:46:08:438] BaseGui::initializeGui: server running on port 36723
 [16:46:08:461] BaseGui::initializeMenus
 [16:46:08:461] BaseGui::updateRecents
 [16:46:08:462] BaseGui::updateWidgets
 [16:46:08:463] BaseGuiPlus::loadConfig
 [16:46:08:463] DefaultGui::createStatusBar
 [16:46:08:464] DefaultGui::createActions
 [16:46:08:465] DefaultGui::createControlWidget
 [16:46:08:465] DefaultGui::createControlWidgetMini
 [16:46:08:486] BaseGui::initializeMenus
 [16:46:08:487] BaseGui::updateRecents
 [16:46:08:487] DefaultGui::updateWidgets
 [16:46:08:487] BaseGui::updateWidgets
 [16:46:08:490] DefaultGui::loadConfig
 [16:46:08:490] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:1024
 [16:46:08:490] ToolbarEditor::load: 'toolbar1'
 [16:46:08:490] ToolbarEditor::load: loading action open_file
 [16:46:08:491] ToolbarEditor::load: loading action open_dvd
 [16:46:08:491] ToolbarEditor::load: loading action open_url
 [16:46:08:491] ToolbarEditor::load: loading action separator
 [16:46:08:491] ToolbarEditor::load: adding separator
 [16:46:08:491] ToolbarEditor::load: loading action compact
 [16:46:08:491] ToolbarEditor::load: loading action fullscreen
 [16:46:08:491] ToolbarEditor::load: loading action separator
 [16:46:08:491] ToolbarEditor::load: adding separator
 [16:46:08:491] ToolbarEditor::load: loading action screenshot
 [16:46:08:491] ToolbarEditor::load: loading action separator
 [16:46:08:491] ToolbarEditor::load: adding separator
 [16:46:08:491] ToolbarEditor::load: loading action show_file_properties
 [16:46:08:492] ToolbarEditor::load: loading action show_playlist
 [16:46:08:492] ToolbarEditor::load: loading action show_preferences
 [16:46:08:492] ToolbarEditor::load: loading action separator
 [16:46:08:492] ToolbarEditor::load: adding separator
 [16:46:08:492] ToolbarEditor::load: loading action play_prev
 [16:46:08:492] ToolbarEditor::load: loading action play_next
 [16:46:08:492] ToolbarEditor::load: 'controlwidget'
 [16:46:08:492] ToolbarEditor::load: loading action play
 [16:46:08:492] ToolbarEditor::load: loading action pause_and_frame_step
 [16:46:08:492] ToolbarEditor::load: loading action stop
 [16:46:08:493] ToolbarEditor::load: loading action separator
 [16:46:08:493] ToolbarEditor::load: adding separator
 [16:46:08:493] ToolbarEditor::load: loading action rewindbutton_action
 [16:46:08:493] ToolbarEditor::load: loading action timeslider_action
 [16:46:08:493] TimeSlider::setDragDelay: 100
 [16:46:08:493] ToolbarEditor::load: loading action forwardbutton_action
 [16:46:08:493] ToolbarEditor::load: loading action separator
 [16:46:08:493] ToolbarEditor::load: adding separator
 [16:46:08:493] ToolbarEditor::load: loading action fullscreen
 [16:46:08:493] ToolbarEditor::load: loading action mute
 [16:46:08:494] ToolbarEditor::load: loading action volumeslider_action
 [16:46:08:494] ToolbarEditor::load: 'controlwidget_mini'
 [16:46:08:494] ToolbarEditor::load: loading action play_or_pause
 [16:46:08:494] ToolbarEditor::load: loading action stop
 [16:46:08:494] ToolbarEditor::load: loading action separator
 [16:46:08:494] ToolbarEditor::load: adding separator
 [16:46:08:494] ToolbarEditor::load: loading action rewind1
 [16:46:08:494] ToolbarEditor::load: loading action timeslider_action
 [16:46:08:494] TimeSlider::setDragDelay: 100
 [16:46:08:494] ToolbarEditor::load: loading action forward1
 [16:46:08:495] ToolbarEditor::load: loading action separator
 [16:46:08:495] ToolbarEditor::load: adding separator
 [16:46:08:495] ToolbarEditor::load: loading action mute
 [16:46:08:495] ToolbarEditor::load: loading action volumeslider_action
 [16:46:08:495] ToolbarEditor::load: ''
 [16:46:08:495] ToolbarEditor::load: loading action play
 [16:46:08:496] ToolbarEditor::load: loading action pause
 [16:46:08:496] ToolbarEditor::load: loading action stop
 [16:46:08:496] ToolbarEditor::load: loading action separator
 [16:46:08:496] ToolbarEditor::load: adding separator
 [16:46:08:496] ToolbarEditor::load: loading action rewindbutton_action
 [16:46:08:496] ToolbarEditor::load: loading action timeslider_action
 [16:46:08:497] TimeSlider::setDragDelay: 100
 [16:46:08:497] ToolbarEditor::load: loading action forwardbutton_action
 [16:46:08:497] ToolbarEditor::load: loading action separator
 [16:46:08:497] ToolbarEditor::load: adding separator
 [16:46:08:497] ToolbarEditor::load: loading action fullscreen
 [16:46:08:497] ToolbarEditor::load: loading action mute
 [16:46:08:497] ToolbarEditor::load: loading action volumeslider_action
 [16:46:08:497] ToolbarEditor::load: loading action separator
 [16:46:08:497] ToolbarEditor::load: adding separator
 [16:46:08:498] ToolbarEditor::load: loading action timelabel_action
 [16:46:08:499] Helper::qtVersion: 4602
 [16:46:08:501] DefaultGui::loadConfig: playlist visible: 0
 [16:46:08:501] DefaultGui::loadConfig: playlist position: 0, 0
 [16:46:08:501] DefaultGui::loadConfig: playlist size: 100 x 30
 [16:46:08:501] DefaultGui::updateWidgets
 [16:46:08:501] BaseGui::updateWidgets
 [16:46:08:510] BaseGui::showEvent
 [16:46:08:512] main: remove_lock: /home/ofir/.config/smplayer/smplayer_init.lock
 [16:46:08:516] BaseGui::loadActions
 [16:46:08:516] ActionsEditor::loadFromConfig
 [16:46:08:648] BaseGui::initializeMenus
 [16:46:08:648] BaseGui::updateRecents
 [16:46:08:650] DefaultGui::updateWidgets
 [16:46:08:650] BaseGui::updateWidgets
 [16:46:10:623] BaseGui::fileOpen
 [16:46:12:282] BaseGui::openFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:283] Core::openFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:283] Core::playNewFile: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:283] Core::saveMediaInfo
 [16:46:12:283] FileSettingsHash::existSettingsFor: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:285] FileSettingsHash::existSettingsFor: config_file: '/home/ofir/.config/smplayer/file_settings/f/f0ed5a78080a4ade.ini'
 [16:46:12:285] Core::playNewFile: We have settings for this file!!!
 [16:46:12:285] FileSettings::loadSettingsFor: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:287] FileSettingsHash::loadSettingsFor: config_file: '/home/ofir/.config/smplayer/file_settings/f/f0ed5a78080a4ade.ini'
 [16:46:12:288] MediaSettings::load
 [16:46:12:288] Core::playNewFile: Media settings read
 [16:46:12:288] BaseGuiPlus::resizeWindow: 720, 400
 [16:46:12:288] BaseGui::resizeWindow: 720, 400
 [16:46:12:288] BaseGui::resizeWindow: size to scale: 720, 400
 [16:46:12:288] BaseGui::resizeWindow: the panel size is already the required size. Doing nothing.
 [16:46:12:288] Core::changeAspectRatio: 1
 [16:46:12:289] Core::displayMessage
 [16:46:12:289] Core::playNewFile: volume: 40, old_volume: 40
 [16:46:12:289] Core::initPlaying
 [16:46:12:289] Core::startMplayer
 [16:46:12:289] Core::startMplayer: setting working directory to '/home/ofir/.config/smplayer/screenshots'
 [16:46:12:289] MplayerVersion::isMplayerAtLeast: comparing 27667 with 31044
 [16:46:12:289] MplayerVersion::isMplayerAtLeast: comparing 29058 with 31044
 [16:46:12:289] Core::startMplayer: * not using -colorkey for xv
 [16:46:12:289] Core::startMplayer: * report if you can't see the video
 [16:46:12:290] MplayerVersion::isMplayerAtLeast: comparing 27872 with 31044
 [16:46:12:290] MplayerVersion::isMplayerAtLeast: comparing 24924 with 31044
 [16:46:12:290] Core::startMplayer: file basename: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON'
 [16:46:12:291] Core::startMplayer: edl file: ''
 [16:46:12:291] MplayerLayer::playingStarted
 [16:46:12:291] Screen::playingStarted
 [16:46:12:291] Screen::setAutoHideCursor: 1
 [16:46:12:291] Screen::playingStarted
 [16:46:12:291] Screen::setAutoHideCursor: 1
 [16:46:12:291] Core::startMplayer: command: '/usr/local/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/ofir/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:he:ISO-8859-8 -vid 0 -aid 1 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:296] Playlist::setModified: 0
 [16:46:12:296] Playlist::addFiles
 [16:46:12:298] Playlist::addItem: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:299] Playlist::updateView
 [16:46:12:299] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:12:300] Playlist::addFiles: latest_dir: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON'
 [16:46:12:327] MplayerProcess::parseLine: 'MPlayer SVN-r31044-4.4.3 (C) 2000-2010 MPlayer Team'
 [16:46:12:331] MplayerVersion::mplayerVersion: MPlayer SVN revision found: 31044
 [16:46:12:332] MplayerProcess::parseLine: MPlayer SVN: 31044
 [16:46:12:337] MplayerProcess::parseLine: ''
 [16:46:12:338] MplayerProcess::parseLine: 'Playing /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi.'
 [16:46:12:338] MplayerProcess::parseLine: ''
 [16:46:12:538] MplayerProcess::parseLine: 'Cache fill:  0.00% (0 bytes)   '
 [16:46:12:538] Core::displayMessage
 [16:46:12:543] MplayerProcess::parseLine: 'AVI file format detected.'
 [16:46:12:543] MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
 [16:46:12:543] MplayerProcess::parseLine: ID_VIDEO_ID: 0
 [16:46:12:543] MplayerProcess::parseLine: '[aviheader] Video stream found, -vid 0'
 [16:46:12:543] MplayerProcess::parseLine: 'ID_AUDIO_ID=1'
 [16:46:12:543] MplayerProcess::parseLine: ID_AUDIO_ID: 1
 [16:46:12:543] MplayerProcess::parseLine: '[aviheader] Audio stream found, -aid 1'
 [16:46:12:870] MplayerProcess::parseLine: 'AVI: ODML: Building ODML index (2 superindexchunks).'
 [16:46:13:333] MplayerProcess::parseLine: 'VIDEO:  [XVID]  720x400  24bpp  23.976 fps  1475.5 kbps (180.1 kbyte/s)'
 [16:46:13:334] MplayerProcess::parseLine: 'Clip info:'
 [16:46:13:334] MplayerProcess::parseLine: ' Software: VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:46:13:334] MplayerProcess::parseLine: clip_software: 'VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:46:13:334] MplayerProcess::parseLine: 'ID_CLIP_INFO_NAME0=Software'
 [16:46:13:335] MplayerProcess::parseLine: 'ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2542/release)'
 [16:46:13:335] MplayerProcess::parseLine: 'ID_CLIP_INFO_N=1'
 [16:46:13:336] MplayerProcess::parseLine: 'SUB: error opening iconv descriptor.'
 [16:46:13:359] MplayerProcess::parseLine: '[***] Error opening iconv descriptor'
 [16:46:13:359] MplayerProcess::parseLine: '[***] Error recoding file'
 [16:46:13:359] MplayerProcess::parseLine: '[***] Error opening iconv descriptor'
 [16:46:13:360] MplayerProcess::parseLine: '[***] Error recoding file'
 [16:46:13:364] MplayerProcess::parseLine: 'ID_FILE_SUB_ID=0'
 [16:46:13:364] SubTracks::parse: 'ID_FILE_SUB_ID=0'
 [16:46:13:365] SubTracks::find: item type: 2, ID: 0 doesn't exist
 [16:46:13:365] MplayerProcess::parseLine: 'ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:46:13:365] SubTracks::parse: 'ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:46:13:366] MplayerProcess::parseLine: 'SUB: Added subtitle file (1): /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt'
 [16:46:13:366] MplayerProcess::parseLine: 'ID_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:13:367] MplayerProcess::parseLine: 'ID_DEMUXER=avi'
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=XVID'
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=1475456'
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=720'
 [16:46:13:367] MplayerProcess::parseLine: md.video_width set to 720
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=400'
 [16:46:13:367] MplayerProcess::parseLine: md.video_height set to 400
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_FPS=23.976'
 [16:46:13:367] MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=0.0000'
 [16:46:13:368] MplayerProcess::parseLine: md.video_aspect set to 1.800000
 [16:46:13:368] MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=8192'
 [16:46:13:368] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=448000'
 [16:46:13:368] MplayerProcess::parseLine: 'ID_AUDIO_RATE=0'
 [16:46:13:368] MplayerProcess::parseLine: 'ID_AUDIO_NCH=0'
 [16:46:13:368] MplayerProcess::parseLine: 'ID_LENGTH=9702.03'
 [16:46:13:368] MplayerProcess::parseLine: md.duration set to 9702.030000
 [16:46:13:368] MplayerProcess::parseLine: 'ID_SEEKABLE=1'
 [16:46:13:369] MplayerProcess::parseLine: 'ID_CHAPTERS=0'
 [16:46:13:369] MplayerProcess::parseLine: 'Error opening/initializing the selected video_out (-vo) device.'
 [16:46:13:370] MplayerProcess::parseLine: '=========================================================================='
 [16:46:13:370] MplayerProcess::parseLine: 'Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders'
 [16:46:13:372] MplayerProcess::parseLine: 'AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)'
 [16:46:13:372] MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=448000'
 [16:46:13:372] MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
 [16:46:13:372] MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
 [16:46:13:372] MplayerProcess::parseLine: 'Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)'
 [16:46:13:373] MplayerProcess::parseLine: '=========================================================================='
 [16:46:13:373] MplayerProcess::parseLine: 'No such audio driver 'pulse''
 [16:46:13:373] MplayerProcess::parseLine: 'Could not open/initialize audio device -> no sound.'
 [16:46:13:373] MplayerProcess::parseLine: 'Audio: no sound'
 [16:46:13:373] MplayerProcess::parseLine: 'Video: no video'
 [16:46:13:373] MplayerProcess::parseLine: ''
 [16:46:13:375] MplayerProcess::parseLine: ''
 [16:46:13:375] MplayerProcess::parseLine: 'Exiting... (End of file)'
 [16:46:13:375] MplayerProcess::parseLine: detected end of file
 [16:46:13:375] MplayerProcess::parseLine: 'ID_EXIT=EOF'
 [16:46:13:376] MplayerProcess::parseLine: detected end of file
 [16:46:13:376] Core::finishRestart: --- start ---
 [16:46:13:376] Core::newMediaPlaying: --- start ---
 [16:46:13:376] Core::initializeMenus
 [16:46:13:376] BaseGui::initializeMenus
 [16:46:13:376] MediaData::list
 [16:46:13:376]   filename: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:13:376]   duration: 9702.030000
 [16:46:13:376]   video_width: 720
 [16:46:13:376]   video_height: 400
 [16:46:13:377]   video_aspect: 1.800000
 [16:46:13:377]   type: 0
 [16:46:13:377]   novideo: 0
 [16:46:13:377]   dvd_id: ''
 [16:46:13:377]   initialized: 1
 [16:46:13:377]   chapters: 0
 [16:46:13:377]   Subs:
 [16:46:13:377]   Programs:
 [16:46:13:377]   Videos:
 [16:46:13:377] Tracks::list: item 0: ID: 0 lang: '' name: ''
 [16:46:13:377]   Audios:
 [16:46:13:377]   Titles:
 [16:46:13:377]   demuxer: 'avi'
 [16:46:13:377]   video_format: 'XVID'
 [16:46:13:377]   audio_format: '8192'
 [16:46:13:377]   video_bitrate: 1475456
 [16:46:13:377]   video_fps: '23.976'
 [16:46:13:377]   audio_bitrate: 448000
 [16:46:13:377]   audio_rate: 48000
 [16:46:13:377]   audio_nch: 2
 [16:46:13:378]   video_codec: ''
 [16:46:13:378]   audio_codec: ''
 [16:46:13:378] MediaSettings::list
 [16:46:13:378]   current_sec: 0.000000
 [16:46:13:378]   current_sub_id: 0
 [16:46:13:378]   current_program_id: -1000
 [16:46:13:378]   current_video_id: 0
 [16:46:13:378]   current_audio_id: 1
 [16:46:13:378]   current_title_id: -1000
 [16:46:13:378]   current_chapter_id: 0
 [16:46:13:378]   current_angle_id: -1000
 [16:46:13:378]   aspect_ratio_id: 1
 [16:46:13:378]   volume: 40
 [16:46:13:378]   mute: 0
 [16:46:13:378]   external_subtitles: ''
 [16:46:13:378]   external_audio: ''
 [16:46:13:378]   sub_delay: 0
 [16:46:13:378]   audio_delay: 0
 [16:46:13:378]   sub_pos: 100
 [16:46:13:379]   sub_scale: 5.000000
 [16:46:13:379]   sub_scale_***: 1.000000
 [16:46:13:379]   brightness: 0
 [16:46:13:379]   contrast: 0
 [16:46:13:379]   gamma: 0
 [16:46:13:379]   hue: 0
 [16:46:13:379]   saturation: 0
 [16:46:13:380]   speed: 1.000000
 [16:46:13:380]   phase_filter: 0
 [16:46:13:380]   current_denoiser: 0
 [16:46:13:380]   deblock_filter: 0
 [16:46:13:380]   dering_filter: 0
 [16:46:13:380]   noise_filter: 0
 [16:46:13:380]   postprocessing_filter: 0
 [16:46:13:380]   upscaling_filter: 0
 [16:46:13:380]   current_deinterlacer: 0
 [16:46:13:380]   add_letterbox: 0
 [16:46:13:380]   karaoke_filter: 0
 [16:46:13:380]   extrastereo_filter: 0
 [16:46:13:380]   volnorm_filter: 0
 [16:46:13:380]   audio_use_channels: 2
 [16:46:13:380]   stereo_mode: 0
 [16:46:13:381]   zoom_factor: 1.000000
 [16:46:13:381]   rotate: -1
 [16:46:13:381]   flip: 0
 [16:46:13:381]   mirror: 0
 [16:46:13:381]   loop: 0
 [16:46:13:381]   A_marker: -1
 [16:46:13:381]   B_marker: -1
 [16:46:13:381]   forced_demuxer: ''
 [16:46:13:381]   forced_video_codec: ''
 [16:46:13:381]   forced_audio_codec: ''
 [16:46:13:381]   original_demuxer: ''
 [16:46:13:381]   original_video_codec: ''
 [16:46:13:381]   original_audio_codec: ''
 [16:46:13:381]   mplayer_additional_options: ''
 [16:46:13:381]   mplayer_additional_video_filters: ''
 [16:46:13:381]   mplayer_additional_audio_filters: ''
 [16:46:13:381]   win_width: 720
 [16:46:13:381]   win_height: 400
 [16:46:13:381]   win_aspect(): 1.800000
 [16:46:13:382]   starting_time: 0.300000
 [16:46:13:382]   is264andHD: 0
 [16:46:13:382] Core::newMediaPlaying: --- end ---
 [16:46:13:382] BaseGui::enterFullscreenOnPlay: arg_start_in_fullscreen: -1, pref->start_in_fullscreen: 0
 [16:46:13:382] Core::changeAspectRatio: 1
 [16:46:13:382] Core::displayMessage
 [16:46:13:383] Core::setVolume: 100
 [16:46:13:383] Core::tellmp: 'volume 100 1'
 [16:46:13:383] Core::updateWidgets
 [16:46:13:383] DefaultGui::updateWidgets
 [16:46:13:383] BaseGui::updateWidgets
 [16:46:13:383] Core::displayMessage
 [16:46:13:383] Core::changeZoom: 1.000000
 [16:46:13:383] Core::displayMessage
 [16:46:13:386] Core::changeSubVisilibity: 1
 [16:46:13:386] Core::tellmp: 'sub_visibility 1'
 [16:46:13:386] Core::displayMessage
 [16:46:13:387] DefaultGui::enableActionsOnPlaying
 [16:46:13:387] BaseGui::enableActionsOnPlaying
 [16:46:13:388] BaseGui::autosaveMplayerLog
 [16:46:13:388] Playlist:: getMediaInfo
 [16:46:13:390] Playlist::updateView
 [16:46:13:390] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:13:390] BaseGuiPlus::updateMediaInfo
 [16:46:13:390] BaseGui::updateMediaInfo
 [16:46:13:391] Core::updateWidgets
 [16:46:13:391] DefaultGui::updateWidgets
 [16:46:13:391] BaseGui::updateWidgets
 [16:46:13:391] Core::finishRestart: --- end ---
 [16:46:13:391] BaseGui::newMediaLoaded
 [16:46:13:391] Recents::addItem: '/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:13:391] BaseGui::updateRecents
 [16:46:13:392] BaseGui::checkPendingActionsToRun
 [16:46:13:392] BaseGui::checkMplayerVersion
 [16:46:13:392] MplayerVersion::isMplayerAtLeast: comparing 25158 with 31044
 [16:46:13:392] Core::checkIfVideoIsHD
 [16:46:13:416] MplayerProcess::gotError: 4
 [16:46:13:417] MplayerLayer::playingStopped
 [16:46:13:417] Screen::playingStopped
 [16:46:13:417] Screen::setAutoHideCursor: 0
 [16:46:13:417] Screen::playingStopped
 [16:46:13:417] Screen::setAutoHideCursor: 0
 [16:46:13:417] BaseGui::showErrorFromMplayer
 [16:46:13:418] MyProcess::procFinished
 [16:46:13:418] MyProcess::procFinished: Bytes available: 0
 [16:46:13:418] MplayerProcess::processFinished: exitCode: 0, status: 0
 [16:46:13:418] MplayerLayer::playingStopped
 [16:46:13:418] Screen::playingStopped
 [16:46:13:418] Screen::setAutoHideCursor: 0
 [16:46:13:418] Screen::playingStopped
 [16:46:13:418] Screen::setAutoHideCursor: 0
 [16:46:13:419] Core::processFinished
 [16:46:13:419] Core::processFinished: we_are_restarting: 0
 [16:46:13:419] Core::processFinished: play has finished!
 [16:46:13:420] Core::processFinished: exit_code: 0
 [16:46:13:420] Core::updateWidgets
 [16:46:13:420] DefaultGui::updateWidgets
 [16:46:13:420] BaseGui::updateWidgets
 [16:46:13:420] DefaultGui::disableActionsOnStop
 [16:46:13:420] BaseGui::disableActionsOnStop
 [16:46:13:422] Playlist::playNext
 [16:46:13:422] Playlist::updateView
 [16:46:13:422] Playlist::updateView: name: 'Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi'
 [16:46:13:422] Playlist::playItem: 1 (count:1)
 [16:46:13:422] Playlist::playItem: out of range
 [16:46:13:422] BaseGui::playlistHasFinished
 [16:46:13:422] BaseGui::playlistHasFinished: arg_close_on_finish: -1, pref->close_on_finish: 0
 [16:46:15:587] Core::changeOSD: 1
 [16:46:15:587] Core::pausing_prefix
 [16:46:15:587] MplayerVersion::isMplayerAtLeast: comparing 27665 with 31044
 [16:46:15:587] Core::tellmp: 'pausing_keep_force osd 1'
 [16:46:15:587] WARNING:  tellmp: no process running: pausing_keep_force osd 1
 [16:46:15:588] Core::updateWidgets
 [16:46:15:588] DefaultGui::updateWidgets
 [16:46:15:588] BaseGui::updateWidgets
 [16:46:18:687] BaseGui::showLog
 

```

and i also have a problem with installing skins and activating gmplayer you can see it in [email]mplayer-users@mplayerhq.hu[/email] 
[http://www.pubbs.net/201004/mplayer/36720-mplayer-users-how-can-i-install-skins-for-gmapleyr.html](http://www.pubbs.net/201004/mplayer/36720-mplayer-users-how-can-i-install-skins-for-gmapleyr.html)

i have no idea what is all this giberish there.

---

### Post by rvm4000 on 2010-04-18
It seems you compiled mplayer without pulse support. Go to the smplayer preferences, general -> audio, and set another audio driver (alsa or oss).

Your build may also lack support for other things, it seems it fails to load the subtitles...

---

### Post by aviramof on 2010-04-18
i don't have alsa there thoughe i installed alsa mixer i set oss this ubuntu install is brand new i formated and installed everything only yesturday but i had this problem with mplayer before the format.

and i don't know why my build lack support for other things i belive i did everything right and it doesn't explaine the problem with the official version 
svn r1.

if you need any more information just tell me.

---

### Post by rvm4000 on 2010-04-18
Does it work with oss?

If there's no support for alsa in mplayer, I guess you didn't install some development packages...

I've just managed to compile mplayer for lucid, you can find packages here:
[https://launchpad.net/~rvm/+archive/testing/+packages](https://launchpad.net/~rvm/+archive/testing/+packages)

Although I don't know if fribidi would work, as the configure log says this:
```
Checking for fribidi with charsets ... no
```

The problem with the official version is that it prints the identification string in a way that smplayer can't recognize, although I think that shouldn't affect subtitles...

---

### Post by aviramof on 2010-04-18
this is what i get with the compiled svn of mplayer:
```
  p, li { white-space: pre-wrap; }  /usr/local/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao oss -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/ofir/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:he:ISO-8859-8 -vid 0 -aid 1 -subpos 100 -volume 100 -cache 2000 -ss 38 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
  MPlayer SVN-r31044-4.4.3 (C) 2000-2010 MPlayer Team
  Playing /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi.
  Cache fill:  0.00% (0 bytes)   
 AVI file format detected.
 ID_VIDEO_ID=0
 [aviheader] Video stream found, -vid 0
 ID_AUDIO_ID=1
 [aviheader] Audio stream found, -aid 1
 AVI: ODML: Building ODML index (2 superindexchunks).
 VIDEO:  [XVID]  720x400  24bpp  23.976 fps  1475.5 kbps (180.1 kbyte/s)
 Clip info:
  Software: VirtualDubMod 1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_NAME0=Software
 ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2542/release)
 ID_CLIP_INFO_N=1
 SUB: error opening iconv descriptor.
 [***] Error opening iconv descriptor
 [***] Error recoding file
 [***] Error opening iconv descriptor
 [***] Error recoding file
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 SUB: Added subtitle file (1): /media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.srt
 ID_FILENAME=/media/&#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON/Avatar.2009.RETAiL.DVDRip.XviD.AC3-ViSiON.avi
 ID_DEMUXER=avi
 ID_VIDEO_FORMAT=XVID
 ID_VIDEO_BITRATE=1475456
 ID_VIDEO_WIDTH=720
 ID_VIDEO_HEIGHT=400
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=9702.03
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Error opening/initializing the selected video_out (-vo) device.
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
 ID_AUDIO_BITRATE=448000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
 ==========================================================================
 AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffac3
 [Mixer] No hardware mixing, inserting volume filter.
 Video: no video
 Starting playback...
   MPlayer interrupted by signal 11 in module: seek
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
 

```with the original videos works but the subtitles are reverse as before.

  installing mplayer_1.0~rc3+svn20090904-0lucid10_i386.deb isn't this version older then the svn version?

it's downloading 2 files now i can't see what files in terminal look like nvidia current and nvidia setting don't know what that got to do with me i have ati card.

---

### Post by rvm4000 on 2010-04-18
Yes, that version is some months old. I'll try to upload a new one soon.

---

### Post by aviramof on 2010-04-18
ok i installed in synaptic i see the new version but what should i set  in smplayer now i still have mplayer svn r1 in /usr/bin/mplayer and the  compiled version in /usr/local/bin/mplayer is there a third mplayer now  who is the new version?

any way not much has changed for now the old version still run videos and audio with bad subtitles and the compile one only run sound now but with no video and no subtitles.

---

### Post by rvm4000 on 2010-04-18
This package should have replaced the official one. So go to the smplayer preferences and change the path to /usr/bin/mplayer

---

### Post by aviramof on 2010-04-18
ok it did updated the mplayer version in /usr/bin/mplayer it's now MPlayer SVN r29643 but but the subtitles are still reverse left to right

i guess this version is still not as good as the svn version who is working fine in gnome-mplayer(but doesn't work with smplayer)

and by the way it did not replaced the svn version when i write mplayer in terminal i still get MPlayer SVN-r31044-4.4.3 (C) 2000-2010 MPlayer Team

---

### Post by rvm4000 on 2010-04-18
I'll try to build a newer version (mplayer-1.0~rc3+svn20100416 ).

---

### Post by aviramof on 2010-04-18
thanks i'm hopping that this package would solve all the problems i have with mplayer and gmplayer skins.

---

### Post by rvm4000 on 2010-04-18
mplayer-1.0~rc3+svn20100416 has been sucessfully compiled. And this time it seems there's fribidi support:
```
Checking for fribidi with charsets ... yes
```

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by aviramof on 2010-04-18
THANK You very much it's working very well with the subtitles in smplayer!!!

i just have one problem now when i write mplayer in terminal i still see MPlayer SVN-r31044-4.4.3 which is the svn version and i still can't get the
gmplayer to work i still get this messege:
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

and even this command doesn't work:
sudo gmplayer -skin /usr/local/share/mplayer/skins/Blue

even though the skin is in the folder Blue how can i get terminal to recognize the new mplayer version?

i tried to install mplayer-gui from synaptic but i guess it's too should be updated sooner or later
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/566055](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/566055)

---

### Post by rvm4000 on 2010-04-18
Try running /usr/bin/gmplayer 

Otherwise it will run the version you compiled (installed in /usr/local/).

But I would suggest to uninstall the version you compiled. If you still have the source tree of mplayer, go to that directory and type "sudo make uninstall".

---

### Post by aviramof on 2010-04-18
i tried sudo make uninstall before from the compile svn version it didn't work but i would try again now. 

i downloaded from here:
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

and i'm not sure there is uninstall there.

i found a shortcut in /usr/bin/ he seem to work.:)

but as i can see now it's not a very good player i can't even open videos that from my ntfs partitions. 

so forget about it smplayer is much better.:):):)

this is the bug of mplayer-gui in synaptic with the new mplayer version.
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/566055](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/566055)

---

### Post by rvm4000 on 2010-04-18
> **aviramof said:**
> i tried sudo make uninstall before from the compile svn version but it didn't work but i would try again now. 

If that doesn't work, delete at least /usr/local/bin/mplayer


> **aviramof said:**
> and i don't have gmplayer in /usr/bin only a shortcut to somewhere most likely the compiled 
version

Yes, gmplayer is a symlink to mplayer. It's normal. Just run it and it will run the mplayer gui.

> **aviramof said:**
> and as i said i can't install mplayer-gui from synaptic now as you can see in the bug report i posted.

My package already installs a mplayer with gui support. That's why the installation of mplayer-gui fails. If you want to install the official mplayer-gui package you'll need to uninstall my package first. But as I said, my package provides a mplayer compiled with gui support, so that shouldn't be necessary.

---

### Post by aviramof on 2010-04-18
i have edited my previous reply a bit this gmplayer is not so good as i see it because he can't browse ntfs partition there is no my computer option in open file option and i don't need mplayer-gui i just wanted to check the skins option but  have enaf video players now :)

as for deleting  /usr/local/bin/mplayer i have tried it in the past and all that happen was a lot of errors when i wrote mplayer in terminal but maybe now it would work better with the new mplayer version.

update:

as i said errors after deleting.

```
sudo rm /usr/local/bin/mplayer
[sudo] password for ofir: 
ofir@ofir-desktop:~$ mplayer
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer UNKNOWN-Ubuntu-RVM (C) 2000-2010 MPlayer Team

```
i guess i could keep the svn version if i want be able to uninstall it and it seem to be that i can't

```

sudo make uninstall
[sudo] password for ofir: 
Makefile:22: config.mak: No such file or directory
make: *** osdep/: Is a directory.  Stop.

```

and maybe update it from time to time but still use your package in smplayer.:)

And again thank you very much for all your help:):):)

---

### Post by mbz99 on 2010-04-18
Another than rvm ppa , called ripps818 , mplayer build for lucid.
 
delete mplayer

    
```
      sudo apt-get remove mplayer
``` 
add ppa    

```
      sudo add-apt-repository ppa:ripps818/coreavc
``` 
update repository

```
 sudo apt-get update
```install mplayer

   
```
      sudo apt-get install mplayer smplayer 
```[IMG]http://www.forum.ubuntuarabs.com/images/smilies/tongue.gif[/IMG]

until rvm build mplayer

[http://img534.imageshack.us/img534/9105/screenshotdp.png](http://img534.imageshack.us/img534/9105/screenshotdp.png)
:popcorn:

ps , added to rvm

thank anyway

---

### Post by aviramof on 2010-04-18
i didn't understand there is another ppa with mplayer for lucid called 
ripps818/coreavc 
[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

it's a method to install coreavc but rvm build is much newer if i would 
want to install core avc rvm build is still better but thanks for the information
and the ppa.

---

