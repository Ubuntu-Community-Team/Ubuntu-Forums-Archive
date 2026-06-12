---
title: "How I Fixed Static, Pops and Crackles"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-04-14
Gday folks :)

Thought I would share my fix for those annoying pops and crackles I was getting through my speakers.

In the volume control preferences I went and enabled all the optional volume settings, switches and everything. Then, I simply went through and made all of the types that I dont use 0% and muted them. Now I can run my volume on 100% for wave, synth, LFE, front speakers and master without problems.

---

### Post by balaknair on 2009-04-15
I was having the same issue with sound on my desktop PC(Intel HDA, ALC1200) and what worked was something similar to what you tried- Volume Properties> Switches tab> uncheck 'Headphones'

The trouble with that is I use the mic on my headset to chat on skype and so I have to adjust settings again just for that.

The stuff that you muted, does it include the microphones?

---

### Post by Scotty Bones on 2009-04-15
I had this same issue myself. I was able to resolve it by muting the mic. I was playing around in the PulseAudio volume control after adding a second audio card, when I noticed that the volume indicator for the mic on my default card was jumping. However, I have no mic installed, so it wasn't a big deal to mute it. 

I don't know if my approach would help anyone else as I experienced the same behavior when running windows, so I know it is not strictly a Linux or PulseAudio issue.

---

### Post by kansasnoob on 2009-04-15
That is why I always install gnome-alsamixer!

It's ALL in front of you!

---

### Post by Zorael on 2009-04-15
Some static/pops can be caused by alsa driver quirks, in which case you'd need to manually pass a model to it. See [http://ubuntuforums.org/showthread.php?p=5017453#post5017453](http://ubuntuforums.org/showthread.php?p=5017453#post5017453).

---

