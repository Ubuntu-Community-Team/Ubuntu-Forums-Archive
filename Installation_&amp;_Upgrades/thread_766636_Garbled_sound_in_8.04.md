---
title: "Garbled sound in 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by glendavee on 2008-04-25
I've just upgraded to 8.04 from 7.10. Everything seemed to go ok, but now when I try to listen to radio online, I'm getting very garbled sound. Any suggestions on where I should look for a fix?

---

### Post by glendavee on 2008-04-25
More on sound. No problem listening to stored music via Banshee or Rythmbox.
Another issue is that I can't open Synaptic Package Manager, or anything else under Systems>Administration

---

### Post by TDogg310 on 2008-04-26
I'm having the same issue.  I used the alternate install disc to perform the upgrade from Gutsy Gibbon to Hardy Heron.  Everything seems to have installed correctly, but my sound is really garbled.  I am using an HP DV6000 laptop with an HDA Intel sound card.

---

### Post by legendnz on 2008-04-26
If your sound is scratchy and broken up, try right-clicking on the sound icon and selecting "Open volume control". From there, click on the Switches tab and de-selecting "Audio Analogue/Digital Output Jack".

Hope this helps :)

---

### Post by TDogg310 on 2008-04-26
I've been able to fix the problem by reducing the level of PCM on the volume control.

---

### Post by glendavee on 2008-04-27
My volume Control doesn't have the "switch"tab??  I've tried fiddling with the PCM level - no joy.

---

### Post by kunami on 2008-04-27
What the hell? This actually worked for me! :D
Thank you, kind sir.

---

### Post by Phidaux on 2009-05-25
So, my box has had gnarly garbled underwater sounding audio since I upgraded to 9.04

And just now... Whammo, holy crap! I got it fixed-ish!
After 10+ freakin hours of googling on this, reinstalling the drivers and SO many colorful euphemisms spewed from my mouth at my poor lil computer. 

I figured it out... on Kubuntu

1) open up volume mixer

2) settings > configure channels

3) click on SPLIT CHANNEL on PCM 

4) slide the left (or right if that doesn't work... duh) channel all the way down... and tah-freakin-dah... no more underwater audio.


Yea... this really sucked to try and figure out... I just wish that I had this lightning bolt of shear desperation 3 months ago.


I hope this helps.

M

oh and I'm useing a Nvidia CK804

---

### Post by tuflus on 2009-10-21
The split channel fix actually worked for me! I still can't believe that was it. I guess common sense just wasn't gonna help with this one :)

---

