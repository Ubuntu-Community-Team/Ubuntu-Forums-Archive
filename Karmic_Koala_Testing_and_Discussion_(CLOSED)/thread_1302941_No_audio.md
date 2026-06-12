---
title: "No audio"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by K0BA on 2009-10-27
Hello all. I've read a few posts from people who've had sound problems in Karmic, but none of them seem to be quite the same as mine.

Basically, I have no audio. The volume is switched all the way up to 11 on all my sliders, but still nothing.

In Sound Preferences, the Hardware tab shows no hardware. The Output tab lists a "Dummy Output".

When I put ```
cat /proc/asound/card0/codec#* | grep Codec
``` into terminal, this is what I see:

```
Codec: Realtek ALC268
Codec: Motorola Si3054
```

I've checked in my System Monitor, and Pulse is taking up 1.1MiB. Also, (I'm using Amarok to try and play music) when a track is playing it seems to be playing (I'm judging this by the progress bar) faster than real time. I don't know if that's of any significance but it is odd.

I think that might be of some use to you. It's an Advent laptop. Further hardware details upon request (and perhaps telling me how to get them :p ).

---

### Post by K0BA on 2009-10-27
Oh, and apologies for any newbie mistakes, etc...

---

