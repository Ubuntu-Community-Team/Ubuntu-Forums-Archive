---
title: "Wine/Spotify doesn't work with PulseAudio"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilovebrownies on 2009-10-25
I just did a clean install of Karmic RC, and installed Spotify through Wine.

It works fine by itself from time to time, but if I start Firefox and play a Youtube video while Spotify is playing, Firefox has no sound.

I installed pavucontrol, and only Firefox shows up under applications.

If I start Firefox before Spotify, Firefox gets sound, and Spotify goes crazy, i.e speeded up fuzzy playback/won't play at all.

There also doesn't seem to be any where to disable PulseAudio in Karmic as in Jaunty and previously.

Does anyone know how to fix this?

---

### Post by plun on 2009-10-25
Install the **wine1.2** package which includes latest Wine.

"Stable" wine is just crap with Spotify.

Package info:
[http://packages.ubuntu.com/karmic/wine1.2](http://packages.ubuntu.com/karmic/wine1.2)

---

### Post by ilovebrownies on 2009-10-25
Thanks! This solved my problem :)

---

