---
title: "Audigy 2 ZS Recognition and Surround Sound"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dreamkin on 2009-10-11
Sound for me with my Audigy 2 ZS worked perfectly in 9.04. Now I have a problem with 9.10

The new sound preferences dialog doesn't let me choose a Mixer. Normally I'd choose Alsa mixer for Audigy [SB0350] and just raise the volume on relevant channels to get surround.

Now the new preferences dialog doesn't let me choose a mixer and defaults to Sigmatel as device. It does control sound on my card by the volume levels are entirely wrong. e.g. It mutes all channels when master channel is about 1/4 down or does other weird stuff.

Is there a way to choose a mixer in Karmic or a way to use the older sound preferences dialog...?

---

### Post by ljrmorgan on 2009-10-11
> **dreamkin said:**
> Sound for me with my Audigy 2 ZS worked perfectly in 9.04. Now I have a problem with 9.10

The new sound preferences dialog doesn't let me choose a Mixer. Normally I'd choose Alsa mixer for Audigy [SB0350] and just raise the volume on relevant channels to get surround.

Now the new preferences dialog doesn't let me choose a mixer and defaults to Sigmatel as device. It does control sound on my card by the volume levels are entirely wrong. e.g. It mutes all channels when master channel is about 1/4 down or does other weird stuff.

Is there a way to choose a mixer in Karmic or a way to use the older sound preferences dialog...?

I have the same card, and it isn't a problem for me at all. You can run alsa-mixer from the terminal and set all the different levels there, then use the volume control in the panel to control the master volume, that's what I do. I disabled my on-board sound in the bios. The preferences window has always been fine for me, I can select my card for output, then select a profile (I'm using "Analog stereo output" just now, though when I was at a different flat I had 7.1 set up.) I do remember I had problems initially with Karmic (during the alpha) and pulseaudio, turned out that for some reason all my channels had been muted in alsa-mixer.

---

### Post by dreamkin on 2009-10-11
I had problems at the start with surround. But then they were fixed. As long as I need stereo output things seem fine. It's the 7.1 which is problematic. 

On an unrelated note KDE seems to handle sound much better. I had absolutely no problems using Kubuntu 9.04 or 9.10. It's just I don't want to switch to Kubuntu.

Ah well. Maybe things will be better in release.

---

### Post by ranch hand on 2009-10-11
I do not have that card but I do have an old Audigy1 5.1 card.  Gnome Alsamixer is what I use and it is just great.

---

