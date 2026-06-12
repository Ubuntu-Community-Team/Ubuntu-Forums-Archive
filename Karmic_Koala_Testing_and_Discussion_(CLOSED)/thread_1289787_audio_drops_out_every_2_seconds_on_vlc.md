---
title: "audio drops out every 2 seconds on vlc?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-10-12
after a while of recording, or after playing mpg video simultaneously with mplayer and vlc, the sound stops every second or so and comes back. it is very noticeable. 
rebooting the pc helps and then it eventually comes back. it almost seems like an rhythmic interrupt in the sound. the sound drop out can be heard in the real time while it is recording, just playing, or on playing back the recorded mpg file.

any ideas what this is?
what command to kill and restart pulseaudio?

---

### Post by buzzmandt on 2009-10-12
In vlc i had to go into audio settings of vlc and set it to pulseaudio output

---

### Post by donniezazen on 2009-10-13
> **buzzmandt said:**
> In vlc i had to go into audio settings of vlc and set it to pulseaudio output

Thanks worked like a charm.

---

