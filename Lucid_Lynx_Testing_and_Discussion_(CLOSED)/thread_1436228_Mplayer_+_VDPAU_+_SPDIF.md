---
title: "Mplayer + VDPAU + SPDIF"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by roberthr on 2010-03-22
I have decided to give it Lucid a try. It works almost perfect but I have just realised mplayer does not passthrough surround sound anymore. It complains even on vdpau parameter.

Did anybody manage to make this work with Lucid?

---

### Post by jocko on 2010-03-22
spdif passthrough is not possible with pulseaudio, so you need to set mplayer to use alsa. You also need to make sure it uses hwac3 instead of some ac3 decoder.

This should work from a command line:
```
mplayer -ao alsa -afm hwac3 [COLOR=DarkSlateGray]/path/to/filename[/COLOR]
```

---

### Post by roberthr on 2010-03-22
Oh I do. For quite some time I use this line to play it correctly:

```
mplayer -stop-xscreensaver -fs -subcp cp1250 -subpos 98 -subfont-text-scale 3.3 
-display :0.1  -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau, -ao alsa:device=spdif, 
-ac hwac3,hwdts, FILENAME
```
Now it complains on vdpau and mplayer says "no sound". I tried several combinations but it only works without -vo and -ao but plays only stereo.

---

### Post by roberthr on 2010-03-22
Solved, at least audio part :-)

Lucid seems to have a bit smarter audio  than Karmic. So the correct syntax would be:

```
mplayer -ao alsa,pulse, -ac hwac3,hwdts, FILENAME
```

And so far it plays all audio codecs through SPDIF :-)

Now, I have to find what happened to VDPAU.

---

