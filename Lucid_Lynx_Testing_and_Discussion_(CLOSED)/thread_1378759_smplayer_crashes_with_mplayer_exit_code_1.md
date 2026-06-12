---
title: "smplayer crashes with mplayer exit code: 1"
date: 2010-01-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by _Doc_ on 2010-01-11
I am trying to use smplayer to play a .mkv file and I get a MPlayer Error... Mplayer has finished unexpectedly. Exit code:1 and below is the log file.  Does anyone have an idea of whats wrong?

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 71303505 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/doc/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel  -vf-add screenshot -slices -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/doc/mnt/bittorrent/[DB]_Bleach_252_[C0BE4614].avi

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
Unknown option on the command line: -***
Error parsing option on the command line: -***
MPlayer UNKNOWN-4.4.2 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

---

### Post by mc4man on 2010-01-11
Well it would appear the lucid repo mplayer won't accept either having *** enabled nor disabled (-noass

If there's no preference option to deal with this (rvm would know best) then an mplayer built with libass support  will work fine ( with *** enabled or not

Possibly one from the smplayer/mplayer ppa's ( though I'd think there no lucid specific builds.

A [self built mplayer]("http://ubuntuforums.org/showthread.php?t=1305181") works fine here (as mplayer-nogui or with smplayer

This will work ok for lucid to some extent ( depending on graphics's drivers, whether vdpau  and or opengl support is desired some adjustments would be needed (edit - some updates today have resolved opengl as far as building
( have a decent mplayer build on lucid atm

> doug@doug-desktop:~$ mplayer
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r30230-4.4.3 (C) 2000-2009 MPlayer Team


---

### Post by rvm4000 on 2010-01-12
> **_Doc_ said:**
> I am trying to use smplayer to play a .mkv file and I get a MPlayer Error... Mplayer has finished unexpectedly. Exit code:1 and below is the log file.  Does anyone have an idea of whats wrong?

It seems the mplayer you're using has been compiled without a_s_s support.

As workaround, You can uncheck the option "Freetype support" in Preferences -> Subtitles, but subtitles may not display properly.

---

### Post by _Doc_ on 2010-01-12
Thanks for the update... subtitles are a big part of the movies/showes I watch so I will have to find another mplayer with -a_s_s support.  Is there a PPA or a location I can find a precompiled version? I can compile but would like to avoid it if possible.  I believe the mplayer I am using is the version from the ubuntu repos.

---

### Post by rvm4000 on 2010-01-12
You can find in my PPA packages for several versions of ubuntu:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by mc4man on 2010-01-12
The mplayer in lucid is basically the same one used in karmic with only a couple of [changes]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu12/changelog"),  I believe liba_s_s is enabled (internal) in both

There definitely is an issue though, I'd think with the mplayer build, not smplayer

If you run the karmic mplayer in lucid, smplayer works, if you run the lucid mplayer in karmic, smplayer also works

So maybe the difference is something the lucid mplayer is built off of that's been changed and related ([libfreetype ...?]("http://changelogs.ubuntu.com/changelogs/pool/main/f/freetype/freetype_2.3.11-1ubuntu2/changelog")

---

### Post by mc4man on 2010-01-16
Believe if they rebuild mplayer then it will work with cli options involving -a_s_s
bug filed [here]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/508561"), though may end up a dup of a smplayer bug, could use a confirm

---

### Post by pickarooney on 2010-02-26
I have this exact same issue with Jaunty (repository build and SVN version). The crashes happen mostly with subtitles enabled (about 90% of the time for me). Are the three stars in all the posts above supposed to be ay ess ess? (weird swear filter!)? If so, what does it stand for?

---

### Post by rvm4000 on 2010-02-26
What version of mplayer do you have installed in Jaunty? If you're using the old 1.0rc2 I suggest to update it.

---

