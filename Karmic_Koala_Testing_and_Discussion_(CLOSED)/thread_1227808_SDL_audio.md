---
title: "SDL audio"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-07-31
I'm not getting audio out of any SDL apps.

To attempt to see why, I ran a SDL game from a terminal and saw: SDLMixerAudio: Unable to open audio!

Other applications (eg frozen-bubble) aren't giving me that error but are similarly silent.

Magic. What do I need to hump to get SDL sound working? 

(It's entirely possible I have broken things so if you think SDL sound works out the box, please give me some ideas on what I may have knackered)

---

### Post by OliW on 2009-07-31
> **OliW said:**
> (It's entirely possible I have broken things so if you think SDL sound works out the box, please give me some ideas on what I may have knackered)

Well I reinstalled libsdl1.2debian-pulseaudio (god knows why that was swapped out) and that has fixed nexuiz and some other things.

frozen-bubble and gens are still soundless :(

---

### Post by amano on 2009-07-31
Is there a bug for the libsdl1.2debian-pulseaudio problems already?

---

