---
title: "VLC having issues with mp4a and avc1?"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-09-14
I am having problems with vlc 1.0.1 failing to play fairly standard mp4 files (H.264 video codec, AAC audio codec).  

It also looks like it doesn't use libx264.

---

### Post by caryb on 2009-09-14
Wont play wmv files either, Mind you I don't hold it against vlc for that one:lolflag:

Cary

---

### Post by mc4man on 2009-09-14
Vlc can play all those files though the repo version is slightly 'neutered'.

Also versions 1.x.x have a slight issue with wma3 and wmal audio, playback is possible with some limitations  and or alterations. (that would include video with wma3 or wmal audio

Edit: Doing a full install of a6 (vs. live cd), Now have no isses whatsoever with any wma files. 
The difference between the the glibc in hardy and karmic made all the difference

For mp4a, ect. search ffmpeg in synaptic and mark the various ffmpeg libs to install the 'extra' versions (libavcodec52, libavformat52, .......

Don't remove the existing ones, just mark the extra ver.'s and synaptic will 'upgrade'

---

### Post by michael37 on 2009-09-15
> **mc4man said:**
> Vlc can play all those files though the repo version is slightly 'neutered'.

Also versions 1.x.x have a slight issue with wma3 and wmal audio, playback is possible with some limitations  and or alterations. (that would include video with wma3 or wmal audio

For mp4a, ect. search ffmpeg in synaptic and mark the various ffmpeg libs to install the 'extra' versions (libavcodec52, libavformat52, .......

Don't remove the existing ones, just mark the extra ver.'s and synaptic will 'upgrade'

All "extra" packages are already installed.

Curiously,  libavcodec52 itself is not installed.  If I try to install libavcodec52, it asks me whether I want to uninstall gnomebaker, vlc, ffmpeg and everything else.  How nice.

---

