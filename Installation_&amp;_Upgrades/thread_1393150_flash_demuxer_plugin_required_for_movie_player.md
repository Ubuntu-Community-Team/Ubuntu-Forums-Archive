---
title: "flash demuxer plugin required for movie player"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by akhila phadnis on 2010-01-29
hello,
the movie player which i have installed cannot play .flv files. it says, 'flash demuxer' is the required plugin' which is not found... what should i install to make movie player to play .flv files??

---

### Post by mc4man on 2010-01-29
The gstreamer ffmpeg plug-in (if your player is a gstreamer player, if not then specify what 'player'
Or grab these anyway

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

Karmic **sometimes** requires a restart when adding codecs, plugins, ect.

---

