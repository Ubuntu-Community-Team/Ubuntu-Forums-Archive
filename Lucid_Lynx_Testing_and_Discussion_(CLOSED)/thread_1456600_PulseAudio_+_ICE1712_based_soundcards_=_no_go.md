---
title: "PulseAudio + ICE1712 based soundcards = no go"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drucer on 2010-04-17
Release after release it appears that Ubuntu audio system just keeps on being incompatible with ICE1712 chip based professional audio cards like M-Audio Delta series. ICE1712 was introduced in early 2000 and Linux in general has supported ICE1712 based cards approximately 8 years. ICE1712 has FULL Alsa support and every function is covered - despite this Ubuntu keeps on lacking support for these cards.

I've learned what I do every time I install new release of Ubuntu. It's simple - I'll start it like this:

"sudo apt-get remove pulse-audio"

And I get sound. However, this is only a partial solution. Audio still does not work with the default GStreamer player for example. It works perfectly with VLC.

Thus I am asking - how can I move Gstreamer player to trashcan and configure Ubuntu Lucid Lynx to use VLC for all video+audio? When I double click *.m3u, .mp3, .wav, .avi, .mov, .mpg etc. I want VLC player to launch instead of Gstreamer. In fact, I want gstreamer complete out of my systems since it has never functioned.

---

### Post by jkxx on 2010-04-17
See my previous thread at [http://ubuntuforums.org/showthread.php?t=1456565]("http://ubuntuforums.org/showthread.php?t=1456565")

I have an Envy24-based card too and have a similar complaint. Apparently the cards do work fine but are misconfigured by default.

While VLC is great on windows, I would advise against installing it in *Ubuntu. It still refuses to save its preferences and too often gulps up all available RAM/CPU. This has been the case since 7.10 and I'm not sure why it's still messed up.

---

