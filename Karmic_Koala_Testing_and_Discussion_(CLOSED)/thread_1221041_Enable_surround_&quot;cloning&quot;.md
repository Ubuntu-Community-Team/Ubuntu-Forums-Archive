---
title: "Enable surround &quot;cloning&quot;"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-07-23
Under Jaunty (and before), I could load up the old volume control and check a box that enabled surround cloning (duplicating the sound from the front speakers to the rear speakers if it's just a stereo signal).

Under Karmic, I can't see how to do this. I've enabled 5.1 in pavucontrol. 5.1 signals come out the right speakers.

When I open alsamixer, I just see pulseaudio.

Another strange thing is in pavucontrol, my sound card is listed as "Internal Audio".

I basically have no clue what's going on with sound inside Karmic but I need to enable the surround cloning. Any ideas are welcome.

---

### Post by psyke83 on 2009-07-23
Try:

```
$ gnome-volume-control
```

OR:

```
$ alsamixer -Dhw
```

---

### Post by OliW on 2009-07-23
> **psyke83 said:**
> ```
$ gnome-volume-control
```
Brings up the new one.

> **psyke83 said:**
> ```
$ alsamixer -Dhw
```
Brings up a decent mixer! But it doesn't have the options/switches that the old mixer did.

---

### Post by wayne_cat on 2009-07-23
> **OliW said:**
> 

Brings up a decent mixer! But it doesn't have the options/switches that the old mixer did.

You can switch to further settings with the tab key

---

### Post by durand on 2009-07-23
> **psyke83 said:**
> Try:
```
$ alsamixer -Dhw
```

Thanks for that! For some reason, my PCM sound was set at 4% and I couldn't change it from any other volume control...

---

### Post by OliW on 2009-07-23
> **wayne_cat said:**
> You can switch to further settings with the tab key

Not on mine :confused: I only have Playback/Capture/All

---

