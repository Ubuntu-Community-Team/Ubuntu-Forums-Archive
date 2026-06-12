---
title: "Hardware Damage by Intrepid?"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philbo on 2008-09-26
After reading the post "Intrepid tester WARNING: Corruption of Intel e1000e Gigabit Cards", I have been thinking that my issues with my graphics card may be related? 

Forgive my ignorance, but is this possible? Prior to installing and testing Intrepid, I had no (known) problems with my generic Nvidia FX 5200 video card. But since I have had issues with any 3D applications (have tested two O/S I am dual booting in XP for games and have issues with video card).

I have tested in ubuntu and get weird problem with any advanced graphics function (using 173.14.12 Nvidia kernal modules).

Is it just coincidental or has something similar happening with Video cards?

thx 

Philbo

---

### Post by syko21 on 2008-09-26
The e1000e issue stops the hardware from functioning. You seem to be able use the hardware in this case since you can see video. If you could directly name the issues it would certainly help in determining what kind of problem you are having. It may also be a coincidence with a problem with the card, I remember my card's fan stopped working and I couldn't figure out why for the longest time until I looked in the case. If you are seeing especially slow performance or random artifacts in your 3D applications a temperature issue is the most likely cause.

---

### Post by Jack M. on 2008-09-26
It's definitely not related to the network card issue, since that's an issue with the specific piece of firmware used with that particular network card. I had some problems with my GeForce 6800 after trying out suspend in Ubuntu, and it turned out that the hardware was damaged and needed to be replaced. The suspend/Ubuntu was the immediate cause of the problem, but it wasn't at fault, since the card had, unbeknownst to me, been slightly damaged for a while. I can assume this because it turned out that the replacement card (the same model) got much better frame rates in 3D applications than my old one ever did. This isn't necessarily the case here, but it's something to keep in mind if nothing else seems to work.

---

