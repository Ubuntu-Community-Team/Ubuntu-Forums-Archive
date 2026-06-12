---
title: "Karmic Chaos"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cj100570 on 2009-10-23
Seeing as how there are only 6 days until Karmic is released I figured I'd go ahead and install the RC to give it a spin to see if there were going to be any show stoppers with my machine. And what do you know, the same old issue that seems to keep plaguing Ubuntu releases has once again bitten me in the backside, sound doesn't work correctly. Unlike the last 2 releases the only problem I'm having this time is that I can't seem to get the sound from my tv tuner card to play. When I fiddle around with the sound settings there aren't separate sliders like in Jaunty. I don't understand why this continues to be an issue. Why must each release make doing simple things, like adjusting individual sound levels, an exercise in futility? My sound system is a 5.1 system and all speakers are working but I can't get the sound from the line in. With that said I'd appreciate any help that anyone can offer. My system specs are as follows;

EVGA 680i Mobo 
Intel Q6600 
EVGA e-GeForce 8800 GTS
4GB Corsair PC-8500 
1 TB Seagate HD 
2 Lite-On DVD Drives 
Mitsumi Floppy Drive/Media Card Reader 
OCZ 700 Watt PSU
Zalman CNPS9700 NT

---

### Post by silvagroup on 2009-10-23
I think there is a major regression in the Keramic kernel (2.6.30) which started some where after 2.6.27-11. I have tried up to the 2.6.31-020631 which just locks up the system.
On my HP DV 5 any kernel after 2.6.27-11 looses sound and with some kernels looses wifi also and like I said the.31 kernels just die.
So right now I am pretty much stuck at 2.6.27-11 so Keramic certainly won't be an option here any time soon.

This maybe Intel chip-set specific because the 2.6.28 kernel versions so far work OK on Nvidia chip-sets which is on my desktop unit, also HP.
I'll have to test Keramic on my desktop to see how that behaves before I upgrade to it.

---

### Post by dabl on 2009-10-23
It is indeed a frustrating thing to have to fix the sound system on what should be an "improved" version of the OS.

Your problem is totally irrelevant to "64-bit".  I would say start with the basics -- follow the guidance here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

it should lead you to some sort of success.  :)

---

### Post by cj100570 on 2009-10-23
> **silvagroup said:**
> I think there is a major regression in the Keramic kernel (2.6.30) which started some where after 2.6.27-11. I have tried up to the 2.6.31-020631 which just locks up the system.
On my HP DV 5 any kernel after 2.6.27-11 looses sound and with some kernels looses wifi also and like I said the.31 kernels just die.
So right now I am pretty much stuck at 2.6.27-11 so Keramic certainly won't be an option here any time soon.

This maybe Intel chip-set specific because the 2.6.28 kernel versions so far work OK on Nvidia chip-sets which is on my desktop unit, also HP.
I'll have to test Keramic on my desktop to see how that behaves before I upgrade to it.

It's definitely annoying. The wheel doesn't need to be reinvented with each released.

---

### Post by cj100570 on 2009-10-23
> **dabl said:**
> It is indeed a frustrating thing to have to fix the sound system on what should be an "improved" version of the OS.

Your problem is totally irrelevant to "64-bit".  I would say start with the basics -- follow the guidance here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

it should lead you to some sort of success.  :)


Thanks. I'll give the guide a once over.

---

### Post by cj100570 on 2009-10-24
I installed Gnome Alsa Mixer and I'm back in business. It allows me to adjust the channels individually so now I can raise the level on my line in to hear sound from my tuner card.

---

### Post by silvagroup on 2009-10-24
I downloaded the livecd. I had to install broadcom driver and wifi worked.
Sound at least ogg works on livecd.
But it keeps freezing up on livecd and turning system of is the only way out.

Will wait for final version in few days and try a separate partition install before I commit.

---

