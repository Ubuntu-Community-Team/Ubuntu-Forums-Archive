---
title: "snd_hda_intel sound almost mute at 50%"
date: 2009-01-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-01-27
I have a dell latitude E6400 which works using snd_hda_intel. I have maximized all volumes using alsamixer -Dhw, but if I lower the volume at 50% the audio becomes almost mute. The vol meter should be stretched! 

Do any of you have the same issue? bye

---

### Post by mewithafez on 2009-01-27
> **yelo3 said:**
> I have a dell latitude E6400 which works using snd_hda_intel. I have maximized all volumes using alsamixer -Dhw, but if I lower the volume at 50% the audio becomes almost mute. The vol meter should be stretched! 

Do any of you have the same issue? bye

Yup, using a gateway cx210x the volume is basically 0 when at 50% and 100% at 100%, using any volume bar. This hasn't been that much of a problem for me but I can see how it could be, and it has been like this for 3 or 4 releases.

---

### Post by Gourgi on 2009-01-27
> **mewithafez said:**
> Yup, using a gateway cx210x the volume is basically 0 when at 50% and 100% at 100%, using any volume bar. This hasn't been that much of a problem for me but I can see how it could be, and it has been like this for 3 or 4 releases.

+1 here 
exactly the same behavior since pulseaudio was used

---

### Post by yelo3 on 2009-01-27
Ok, we should file a bug... againsta what package?

---

### Post by cszikszoy on 2009-01-27
Have you tried going to System > Preferences > Sound and adjusting the default mixer?

At the bottom there should be a drop down menu listing all of the sound devices.  Change that to the pulseaudio device, for me it says: "Playback: ALSA PCM on front:0 (ST......) via DMA (PulseAudio...)".  That mixer should only list one track in the box below, highlight that and close.

For me, this fixed the strange volume issues.  I pretty much had the same issue, lowering the volume to about 60% would produce absolutely no sound volume, where 100% would be eardrum-rupturingly-loud.  Since there aren't really that many steps between there wasn't much control over the volume.

After doing this, my volume properly fades based on the percentage that the volume controls report.

---

### Post by yelo3 on 2009-01-27
No dropdown menus for me in jaunty...

---

