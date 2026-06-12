---
title: "Sound Issues."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by PriToX on 2009-11-19
[I]Fixed my problem, my loading snd-atiixp for the snd card, and by commenting out the following from alsa-base.conf:

options snd-hda-intel power_save=10 power_save_controller=N

The main reason (i belive), it wasnt working all to well here, is because of the powersave is on by default. I have always used the intel driver earlier with this card. [/I]

Hey all. 

Ever since ubuntu shipped with pulseaudio, i have had problems after an installation of it (ubuntu).

With pulseaudio, I always get this "distorted sound" when there is a sound/event sound going to play.. The sound plays okey, perfect quality, and i got no problems whatsoever other than this "distorted sound". 

Im on a gigabyte motherboard, using internal soundcard. a realtek something..

In the past, all i had to do, to fix my issues, was to remove pulseaudio, do a "alsaconf",
reboot and it was all done. 

Now, alsaconf seems to be "no more" in ubuntu, and the "regular" volume control for gnome seems to be gone. So, question is, how do i solve this? Pulseaudio has always been a problem on this computer, using this soundcard, and no, putting another snd card in is not an option as there is no room for a such.

Is there an "easy" way i can get rid of pulseaudio and just use "regular" alsa sound?

---

### Post by EMVirostek on 2010-02-06
This might be a stupid question, but what does "comment out" mean?  I'm having the same issue with the sound card.

---

### Post by mikewhatever on 2010-02-06
> **EMVirostek said:**
> This might be a stupid question, but what does "comment out" mean?  I'm having the same issue with the sound card.

This is commented out - the system ignores the line - note the '#' sign:

```
**#**options snd-hda-intel power_save=10 power_save_controller=N
```

---

