---
title: "how do you increase &quot;front&quot; volume in karmic?"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-07-31
Hi,

I have a problem with audio in karmic: it sounds too soft.

To solve that, in jaunty I would open the sound preferences dialogue and crank the "front" slider up, but that option seems to be gone now. I have read this [blog post]("http://www.hadess.net/2009/03/our-new-volume-feature.html") where there is supposed to be a fade slider, which I suppose would have the same effect:

[IMG]http://imgur.com/IAIQX.png[/IMG]

But that is nowhere to be found in my system. Is there a workaround to make my system sound a little louder? Maybe change the card's profile to just a stereo output?

[IMG]http://imgur.com/hXovk.png[/IMG]

Thanks.

---

### Post by Slug71 on 2009-07-31
Its really soft for me too. I think it has something to do with those Pulse updates we got the other day.

---

### Post by terry_gardener on 2009-07-31
does seem a little soft for me but only the voices in dvd movies. 

i have found that you can increase the volume passed 100% in the pulseaudio device chooser package.

and going to manager. 

this might help.

---

### Post by anders_c_ on 2009-07-31
I have a x-fi card and can set my front volume in alsamixer...just run "alsamixer" in a terminal to see the different channels you have.
You could also try to install "pavucontrol" which has different volume sliders for each channel.

---

### Post by iaskedalice09 on 2009-07-31
Try installing gnome-alsamixer with sudo apt-get install gnome-alsamixer -y. I had trouble too until I went in and cranked the Front and Speaker volumes up.

Good luck!

---

### Post by caecusum on 2009-07-31
You should also be able to try:
```
alsamixer -c 0
```

---

### Post by Bou on 2009-07-31
Thanks a bunch guys, just running "alsamixer" does the trick. I guess when the new volume capplet gets that "fade" slider it will handle this?

---

### Post by Regenweald on 2009-07-31
That was indeed the problem. Thanks ! shot attached
use arrows to navigate and +/- to adjust 'front' as i did. mine was at zero. Had to install alsa-utils first though.

---

### Post by cszikszoy on 2009-07-31
You can also try running
```
 
alsamixer -D hw:0

```
in a terminal and checking the slider levels.

---

