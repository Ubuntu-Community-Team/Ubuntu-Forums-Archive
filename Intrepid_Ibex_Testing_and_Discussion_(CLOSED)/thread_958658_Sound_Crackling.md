---
title: "Sound Crackling"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gletob on 2008-10-25
Hi My sound has been work pretty well so far with 8.10 but I updated yesterday and now all I get when I play music or a game a crackling noise comes from my speakers the sound still works fine in windows.

Here is the output of aplay -l
```
owner@glenn-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Aqariun on 2008-10-25
Seems to be a common problem, here's mine

[http://ubuntuforums.org/showthread.php?t=958303](http://ubuntuforums.org/showthread.php?t=958303)

I have tried almost every fix from various threads with no luck.

---

### Post by heavensblade23 on 2008-10-25
Make sure the gain isn't set too high...it could be clipping because it's going above 0db.  Check the CLI alsa mixer.

---

### Post by gletob on 2008-10-25
it's not set too high and The crackling's not constant only when something is playing and no sound but the crackling sound is made

---

