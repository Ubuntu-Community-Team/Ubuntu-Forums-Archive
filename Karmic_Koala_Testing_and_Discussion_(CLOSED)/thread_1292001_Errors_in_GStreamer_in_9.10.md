---
title: "Errors in GStreamer in 9.10"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by YSH on 2009-10-15
I recently installed a fresh copy of the beta of Ubuntu 9.10. However, I can't get it to play any video files.

Ofcourse, I have installed all necessary gstreamer-codecs (which worked in previous releases), but still Totem refuses to play. When I try to play a .mp4 it says there was an error in GStreamer ('GStreamer kwam een algemene stroomfout tegen' / tranlation: 'GStreamer found a general streamingerror.'), and .avi files gives 'Fout in de interne datastroom' / 'Error in the internal datastream'.

Does anyone know what is causing this, and how I can solve it?

---

### Post by mc4man on 2009-10-15
While totem remains fairly worthless for dvd video it can play many A/V formats. ( by no means all, but many

Why don't you search ffmpeg in synaptic and if not installed install the 'extra' versions of the ffmpeg libs. ( libavcodec-extra-52 , libavformat-extra-52, ect. ect.

Don't remove the current, just mark the 'extra' versions and apply.

---

### Post by YSH on 2009-10-15
Thanks, I've tried what you said, but it still doesn't play. I however did notice that Totem displays correctly the length of the movies, but still gives the error.

---

### Post by mc4man on 2009-10-15
Went ahead and booted up a testing karmic where everything is straight up repo packages.
Tried a couple of .avi's (divx5, xvid) and some mp4's (avc/aac) and a .mov.
Totem played them fine.

Wouldn't play a wmv (VC-1/wma3

If you have the gstreamer0.10-ffmpeg plugin installed then don't know myself what the issue is (actually never use totem on my working install other than some of the plugins (internet

For comparision  the repo vlc and mplayer also use libavcodec, ect. Maybe try one of them

If you install the repo ffmpeg itself then in terminal

ffmpeg -i /path/to/file 
will give you some info or

ffplay /path/to/file 
will test whether the repo ffmpeg can decode

(for audio ffplay may need the libsdl1.2debian-pulseaudio package installed

---

### Post by YSH on 2009-10-15
Since ffmpeg didn't want to run (yet was installed), I decided to simply delete all the codecs, and reinstall them using the window Totem prompts when they're not yet installed. This time it worked. I still think it's a bit strange, I reinstalled some packages earlier, but those must have been the wrong ones.

---

