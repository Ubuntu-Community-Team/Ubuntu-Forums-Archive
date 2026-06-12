---
title: "no headphone sound?  8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlh68 on 2008-10-25
I do not have sound on my headphones.  I am using Ubuntu 8.10 on my Acer laptop.  When I click on "Volume Control" its says I am using HDA Intel (Alsa Mixer).  For headphones all is shown is headphone switch.  The headphone jack works in that it will cut off the speakers, but no audio is out at the speakers.

Any help from my Ubuntu colleagues?

---

### Post by Bad_Cop on 2008-10-26
try this. it worked for me. 

> 1. Right click on volume control.
2. Click 'Open Volume Control'
3. Go to Edit --> Preferences
4. Check off 'Surround Sound'
5. Close Preferences
6. Un-mute 'Surround Sound'
7. Plug in headphones

originaly posted [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957").

---

### Post by jlh68 on 2008-10-29
I do not get "Surround Sound" as an option in the Volume Control Menu.  I did on my PC (8.10Beta) and I did just as your tip said and it worked.

Is this one of those "Pulse Audion" problems and ALSA should be used?

---

