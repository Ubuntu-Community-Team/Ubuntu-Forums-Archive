---
title: "sound recording not working"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by irielion on 2005-05-29
Hey, my sound recording is not working.
I used to work on Fedora Core 3 and other distro's.

my recording volume is up, mic for capturing. Input Source Select = Input1
there is no device blocking, the recording (arecord/audacity) simply starts, but there is no sound recorded.

I'm lost in this now, anyone knows something? Please look at my asound.state
My card is via82xx.

thanx in advance

---

### Post by Seti on 2005-06-04
Have you looked at your levels with alsamixer? You have to hit <tab> to display the input levels; I believe they are turned right down by default.
I had the exact same problem ;-)

---

### Post by irielion on 2005-06-04
No my problem was different.
but i managed to solve it. The thing was different, i had to do something with the capture volume and then it would work. I think something change in the alsa driver where i was not aware of.

---

