---
title: "ALAC Decoder + Rhythmbox = FAIL"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garok89 on 2010-04-10
Whilst putting lucid through its paces, I stumbled across an issue I have not encountered in the 2 years I have been using ubuntu.
I went to play some apple-lossless files (Abbey Road) and alac-decoder was not found by rhythmbox or totem.
Manual install failed to reap any results - just another failed codec search.
I have never had this issue in previous released

Can anyone confirm this issue before I submit a bug report?

I will send a lossless file for you to test if necessary

alac-decoder does work fine from the terminal, just not in any gstreamer frontends (totem, rhythmbox,songbird) - vlc works fine.

Installed alac-decoder, libavcodec-unstrippred, gstreamer good bad and ugly - no results

---

### Post by mc4man on 2010-04-10
Well this alac file plays,(lucknight.m4a) if you can maybe test that.
[http://samples.mplayerhq.hu/A-codecs/lossless/](http://samples.mplayerhq.hu/A-codecs/lossless/)

If you can upload a non-playing sample somewhere that would be interesting.
(guess I could create one w/ dbpoweramp on another install to d. ck.

---

### Post by garok89 on 2010-04-10
nup...comes up with "searching for plugins" - which fails
fresh install thismorning as i was switching from 64 to 32bit so i dont see there being dependancy issues....

any chance you could tell me your codec packages please?

```
The playback of this movie requires a Apple Lossless Audio (ALAC) decoder plugin which is not installed.
```

---

### Post by mc4man on 2010-04-10
\,> any chance you could tell me your codec packages please?
I'm on an install I've modded a bit so went to a tester and the linked file played fine, this is what's installed - 

```
gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse

```
(all the current versions
also libavcodec-extra-52

The link also opened directly in firefox w/ totem-mozilla plug-in

(on the link am referring to the .m4a, not the -als.mp4 - that format only plays in ffplay and mplayer, maybe vlc with a little work

---

### Post by garok89 on 2010-04-11
strange, i had the same installed....

i purged gstreamer and everything that goes along with it, reistalled totem, rhythmbox and gnome-codec-installer after a reboot....opened the file and it found the codec in  gstreamer-ffmpeg and played flawlessly

my guess would be that it got confused by me installing them manually and a flag wasnt set

thanks for your help

guess it was the whole "computers dont make mistakes, people using computers make mistakes" thing

---

