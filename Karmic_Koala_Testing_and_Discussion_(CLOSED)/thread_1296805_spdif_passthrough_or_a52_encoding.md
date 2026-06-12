---
title: "spdif passthrough or a52 encoding"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Catscrash on 2009-10-21
Hi,
did anyone get a52 encoding or spdif passthrough working in karmic?

Thx for any help...

---

### Post by Peter09 on 2009-10-21
Install gnome-alsa-mixer, in there you will find the tick box to turn spdif on.

---

### Post by Catscrash on 2009-10-21
thats not what i meant, i spoke about passing a ac3 stream directly to the receiver when watching movies, for example via vlc.

the other thing (a52 encoding) used to work with the a52 alsa-plugin and pulseaudio, that enabled you to create an ac3 stream for yourself which was then send to the receiver.

---

### Post by imaca on 2009-10-22
Don't know enough to help but I have dolby digital via spdif on my nforce2 motherboard using xine.
As above I had to un-mute via alsamixer initially, but some update has changed this, spdif now seems to be independant of alsa.
Quite buggy tho, in hardy I can have analog and digital spdif going quite happily together at same time, this is no longer possible.
For example I just had to shut down tvtime which outputs to analog to try out a dvd and check that I was getting dolby over optical.

---

