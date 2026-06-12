---
title: "Cannot seem to get any media player to reliably work"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-05-29
Greetings.
 
 I am a newbie to linux and i decided to try kubuntu after reading over the webs. I got lastest 10.04 release of kubuntu installed (downloaded yesterday). 
 
So far i dont seem to get any mediaplayer to work correctly with video files (avi's and Video_ts.ifo's). I've tried:

- built in Dragon
- Vlc
- mplayer and kmplayer/smplayer
- xine

the result is as follows

- Dragon plays only Dvd's "vob" files but cannot switch audio or subtitles
- vlc wont open ANYTHING at all
- mplayer crashes on anything as well
- xine will play some videos as dragon but wont play vob files (no "muxer")

At first i installed recommended stuff to play mp3's. When i tried to watch films or dvd's i couldnt do it with Dragon so i tried to install so advertised VLC. I did, and when i open ANY file in VLC, it closes itself. Just closes. Or on rare occasions (when opening some of dvd's files) it just opens a big black screen and reverts to starting small state w/o screen or file opened. I can even sometimes see the first picture from the video blink before it closes. I couldnt get ANY file to play on VLC not even an mp3...
I then installed some packages that told they contain codecs to play alot of formats, and package for "encoded dvd's" - nothing.

After that i've seen that now i can play some videos (avi's and stuff) and even DVD's with built in Dragon video player, but dragon cannot understand subtitles or different audio streams. I tried mplayer and Xine with no luck as well.

now since its not a problem of one player, but i cannot get to play video_ts.ifo files at all and cannot get vlc and mplayer to play anything at all, there must be something i am doing wrong (as a complete linux noob). Could anyone point it out for me please?

---

### Post by kansasnoob on 2010-05-29
I always install the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And you'll want to install "libdvdcss2" and either "w32codecs" or "w64codecs" depending on what version of Kubuntu you installed (64bit or 32bit).

I'd also install "kubuntu-restricted-extras" if it's not already.

Note: you may also need the "alsa-firmware" package from Medibuntu to deal with that sound issue:

[http://ubuntuforums.org/showthread.php?p=9378043#post9378043](http://ubuntuforums.org/showthread.php?p=9378043#post9378043)

---

### Post by Istrebitel on 2010-05-31
Do i understand it correct that "installing a repo" is just adding a repository (a storage area for compilations, software etc) to the list in which the utilities (package managers) look for when i do a search? I come from windows where i was used to just googling and dl'ing an exe so i dont quite know this way of installing stuff.

Okay, so after installing those packages, the vlc and other players should play the videos all right, or should i also change something else? 

PS: I will try that in the evening when i'm back to my linux pc, cant do it now...

---

### Post by Istrebitel on 2010-06-01
Okay the problem was that the default audio output for some odd reason was choosing pulseaudio in VLC. when i switched to UNIX OSS it is now correctly playing dvds, video and audio...

---

