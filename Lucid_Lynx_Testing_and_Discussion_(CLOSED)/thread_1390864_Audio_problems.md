---
title: "Audio problems?"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-01-26
Hardware: Dell Precision M90, Intel HDA

Scenario: Play a track in Rhythmbox. Open Terminal and press backspace a few times.

Result: The track in Rhythmbox stutters.

Solution: Open Volume Control. Under 'Output' tab, select 'Internal Audio Analog Stereo' instead of 'Internal Audio'.

Reason: Smeg knows!

---

### Post by phenest on 2010-01-26
But it has reverted to 'Internal Audio' by itself and the problem has ceased. But, then there is no alert sound played unless I reselect 'Internal Audio Analog Stereo'.

What the smeg is going on?!

---

### Post by phenest on 2010-01-27
How do I get it to stay on the output I select? It reverts back after each boot.

---

### Post by phenest on 2010-02-05
> **phenest said:**
> But, then there is no alert sound played unless I reselect 'Internal Audio Analog Stereo'.

And I cannot mute the volume via the keyboard unless I switch to 'Internal Audio Analog Stereo'.

This is very annoying. A bug needs reporting me thinks.

---

### Post by cristianrosa on 2010-03-20
Hi! I'm a Dell Precision M90 user too, and I'm testing Lucid Beta1 LiveCD.
I have a question, do you have problems with how pulseaudio controls the volumes?.
I have a problem similar to what I have with Karmic, basically when modifying the volume, pulse affects only Master(front speakers) first, then PCM + LFE together. In other words, it considers that LFE is at an innermost level than Master, so in order to raise the volume of the front speakers (master), first PCM and LFE should be to their maximun volume, and that is really loud!
In Karmic I could adjust the volumes individually in alsa mixer, and set pulse to control PCM instead, so it would some how workaround the problem, but in Lucid, I cannot individually change the volumes from alsa mixer, making sound almost unusable.

---

