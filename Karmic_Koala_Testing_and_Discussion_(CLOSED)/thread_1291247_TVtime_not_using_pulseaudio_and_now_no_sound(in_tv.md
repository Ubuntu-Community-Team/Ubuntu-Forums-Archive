---
title: "TVtime not using pulseaudio and now no sound(in tvtime) either."
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-10-14
Hi
I have been using tvtime fine in karmic, even though it doesnt show in the volume control.

But as of recent updates , it gives no sound.

Does anyone know how to route tvtime through pulseaudio?




rajeev

---

### Post by ppjose on 2009-10-14
same problem here

---

### Post by rajeev1204 on 2009-10-14
> **ppjose said:**
> same problem here

was working a few days ago.Stopped with recent updates.

What about you?

---

### Post by ppjose on 2009-10-14
> **rajeev1204 said:**
> was working a few days ago.Stopped with recent updates.

What about you?

not my case then, I only have sound if I run the test on the gstreamer-propierties... 

sorry for my english

---

### Post by rajeev1204 on 2009-10-15
I have solved this problem.
Initially i tried using alsamixer and trying to set CD IN volume slider to max but it didnt work.

Surprisingly, there is something called amixer which actually is a command line tool to control alsa devices and volume where my CD IN was muted.

So using the command ```
amixer -c 0 sset CD,0 80%,80% unmute
```

I got back the sound hoorayyy :)



regards
rajeev

P.S.If someone could clarify the difference between amixer and alsamixer.

---

