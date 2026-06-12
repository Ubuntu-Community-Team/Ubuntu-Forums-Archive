---
title: "Audio pop before a sound plays"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rotarychainsaw on 2009-10-15
Ok new problem here. Started a few days ago after an update. 

When a sound is about to play, I get a pop that comes through my speakers. It sounds the pop that happens sometimes when a computer is first turned on and the speakers are loud. 

This happens if I open any program that is making sounds, like the pop is part of some initialization. Been using this mobo for a while and never had it before. Maybe a new driver or something? 

So... anyone else?

---

### Post by lonniehenry on 2009-10-15
This has been discussed and bugged. You should also bug it also.  It is caused by the sound card powering on and off.  A change in the alsa system to save power. The quick solution is the following.  It basicallly stops the powering cycle. 


sudo gedit /etc/modprobe.d/alsa-base.conf

change line toward end to
options snd-hda-intel power_save=0

reboot and it should end the popping sound.

---

### Post by Rotarychainsaw on 2009-10-15
Ah thank you. Found a relevant bug and put in my 2 cents. I will reboot later and see if your change works.

---

### Post by xl_cheese on 2009-10-16
Powering down the audio codec may save about 50mA

What size of battery do you have on your system and how long does it last on your system?

You can do the math from that to figure out the delta of having the codec awake vs asleep.  Very minimal savings.

---

### Post by Rotarychainsaw on 2009-10-23
My desktop was were I noticed this first. I don't care about saving a little power on the big machine when the thing is popping super loud due to the external amp... On my laptop though I left it cause I can barely hear it.

---

### Post by Retrograde77 on 2009-10-23
Thanks for that :), that popping sound has been annoying the hell out of me.

---

