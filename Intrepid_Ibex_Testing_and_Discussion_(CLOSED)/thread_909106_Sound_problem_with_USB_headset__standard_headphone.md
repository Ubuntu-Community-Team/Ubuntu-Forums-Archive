---
title: "Sound problem with USB headset / standard headphones"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-09-03
I have a USB headset (for Skype) and headphones which plug in to the standard audio sockets (for music, gaming).

I have Sound Preferences -> Devices all set to 'Autodetect'.  The 'Default Mixer Tracks' is set to HDA Intel (Alsa mixer).  The 'Test' button produces sound in my headphones.  However, when I play music or video I get the following mixed results:

Songbird = USB headset
Rhythmbox = headphones
Firefox = USB headset
Smplayer = USB headset
Totem = headphones

Any suggestions on how to make everything play through headphones?  Any thoughts on whether this is a bug or just a configuration issue?

---

### Post by ViRMiN on 2008-09-03
Are you using PulseAudio?  If so, you'll have at least two sinks, one for your sound card, and another for your headset.  You can move you apps between the devices, and set a default sink...

---

### Post by DavidONE on 2008-09-03
Yes, I'm using Pulse.  I went searching for info on 'sinks' and found [http://ubuntuforums.org/showthread.php?t=660648](http://ubuntuforums.org/showthread.php?t=660648) but I'd be stabbing in the dark if I tried any of that.  I couldn't find any info on moving apps between devices - any tips?

---

### Post by mc4100 on 2008-09-03
> **DavidONE said:**
> Yes, I'm using Pulse.  I went searching for info on 'sinks' and found [http://ubuntuforums.org/showthread.php?t=660648](http://ubuntuforums.org/showthread.php?t=660648) but I'd be stabbing in the dark if I tried any of that.  I couldn't find any info on moving apps between devices - any tips?
If the Pulseaudio volume manager isn't already install, do so:
```
sudo apt-get install pavucontrol
```
Then launch it with ALT+F2 ...
```
pavucontrol
```
I don't have it installed anymore, but I think I remember there being an arrow that allows you change a (playing) stream to another sink (i.e., device).

---

### Post by DavidONE on 2008-09-03
That fixed it.  Many thanks.

Am I right thinking this 'messy' situation is because of the transition to PulseAudio?  It seems some parts are controlled by the deprecated Alsa and some by the incoming Pulse.

---

