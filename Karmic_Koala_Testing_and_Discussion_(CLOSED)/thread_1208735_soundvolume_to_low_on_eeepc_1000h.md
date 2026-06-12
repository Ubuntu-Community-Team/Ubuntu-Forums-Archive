---
title: "soundvolume to low on eeepc 1000h"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-07-09
latest updates render my machine with only about 50% of the normal sounvolume all sliders show 100% the vu meters read nomal levels. Is this still a kernel issue?

---

### Post by taavikko on 2009-07-09
> **nyarnon said:**
> latest updates render my machine with only about 50% of the normal sounvolume all sliders show 100% the vu meters read nomal levels. Is this still a kernel issue?

Not probably, Speaker levels are set to more sane levels so that it wont pop them out
```
alsa-utils (1.0.20-2ubuntu1) karmic; urgency=low

  * Merge from debian unstable, remaining changes:
    - debian/init:
      + wait until /usr/bin and /var/lib/alsa exist
      + only display an error when dealing with alsactl if there is no card
        specified
      + Set sane level for 'Speaker' and 'Headphone', needed for Dell Mini 9
        and Dell E series

```

The last line.

You can bump it up via "alsamixer"

---

### Post by nyarnon on 2009-07-09
> **taavikko said:**
> Not probably, Speaker levels are set to more sane levels so that it wont pop them out


The last line.

You can bump it up via "alsamixer"

How my alsa mixer is maxed out? This is ridiculous, nothing pops out anymore especially my chat contacts. Who buys Dell anyway?

---

### Post by wayne_cat on 2009-07-09
> **nyarnon said:**
> latest updates render my machine with only about 50% of the normal sounvolume all sliders show 100% the vu meters read nomal levels. Is this still a kernel issue?

All means .. Master, PCM and Speaker?

---

### Post by nyarnon on 2009-07-09
Just had another update and sound is back to an indeed 'sane' level.

---

### Post by psyke83 on 2009-07-09
> **nyarnon said:**
> How my alsa mixer is maxed out? This is ridiculous, nothing pops out anymore especially my chat contacts. Who buys Dell anyway?

Lots of people. It's more sane to set the default volume level lower, as almost all laptops have no external volume controls (excluding buttons which are really hotkeys for software control).

Both of my laptops' speakers nearly blow out when the login sound plays each time I boot the live CD. I always have to plug in headphones to prevent this from happening.

---

### Post by nyarnon on 2009-07-09
> **psyke83 said:**
> Lots of people. It's more sane to set the default volume level lower.

According to this revealing logic we might aswell switch off sound untill manually turned on. Sorry but a soundlevel should stay what is set as default by the user. It shouldn't depend on any brands options.

---

### Post by psyke83 on 2009-07-09
> **nyarnon said:**
> According to this revealing logic we might aswell switch off sound untill manually turned on. Sorry but a soundlevel should stay what is set as default by the user. It shouldn't depend on any brands options.

Perhaps I missed your point, because you missed mine. I was talking about the default volume level set when you first install Ubuntu (and by extension, when you boot from the Live CD).

I wasn't advocating for the volume level to be modified each time you restart the computer (or to limit the maximum volume that can be changed). Whatever setting the user selects should be saved, of course.

Windows follows the same logic - it sets the default levels to something like 66% on the PCM and Master levels for first boot.

The only "logic" at play is the presumption that *some laptops and computers do not have analog volume controls*. Following from this presumption, it makes sense to reduce the default level (upon first install/first boot after installing) to prevent physical hardware damage.

---

