---
title: "Sound is considerably lower than before."
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roasted on 2008-10-23
Just installed Intrepid 64 bit, and I'm finding with my sound card (Turtle Beach Montego DDL 7.1 PCI card) that it's considerably quieter than it was in Hardy.

Sys-Pref-Sounds yields Alsa as everything. I changed it to pulseaudio (alsa and pulse had the same volume level).

When I go to terminal and type alsamixer, only 1 thing appears... 

It says...

Card - Pulseaudio
Chip - Pulseaudio
View - Playback
Item - Master

And that's it. Master. That's all that's listed. Shouldn't there be more? Such as PCM??

EDIT - in the upper right corner if I right click on the sound icon and hit preferences, I saw my PCM was kinda low. I raised it and on headphones, it seems to be better. However, the real test will be in the morning when I can hook up my stereo and see how loud it gets. But, I'm confident that was the answer to part of my question.

I'm still confused over why in alsamixer only 1 thing shows up. Is it because I'm running pulseaudio? I mean, even when I had alsa selected in sys-sound-pref I still had 1 thing listed under alsamixer.

---

### Post by DavidONE on 2008-10-24
It's a PulseAudio issue.  [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192040](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192040) - I think there was another bug for 8.10, but I couldn't find it just now.

You might want to check Volume Control and make sure 'PCM' and 'Front' are at 100% - that helped mine a little, although it's still not as loud as I'd like.

---

### Post by Roasted on 2008-10-24
Could I switch back entirely to Alsa for comparative reasons?

---

### Post by psyke83 on 2008-10-24
> **Roasted said:**
> Could I switch back entirely to Alsa for comparative reasons?

PulseAudio also incorporates its own volume controls (master and per-application).

First of all:
System -> Preferences -> Sound. Set the Playback options to Autodetect, **and don't change them again**. The options here are misleading (they apply only to GStreamer applications, and the ALSA output actually redirects to PulseAudio if it is running). Always leave it to Autodetect.

To test without PulseAudio:
```
$ pkill pulseaudio
$ totem /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

```

Log out and back in to restore PulseAudio, or simply execute "pulseaudio" via the command line with no arguments.

There's also a comprehensive thread on PulseAudio [here]("http://ubuntuforums.org/showthread.php?t=866965").

---

### Post by Roasted on 2008-10-24
Just curious, if that's the case, why isn't everything set to auto detect out of the box? Or... is it and I just changed it to alsa without realizing it?

---

### Post by psyke83 on 2008-10-24
> **Roasted said:**
> Just curious, if that's the case, why isn't everything set to auto detect out of the box? Or... is it and I just changed it to alsa without realizing it?

Those settings have always been set to Autodetect by default, so you must have changed them (or it has been changed in the RC release, which I doubt).

Look at my PulseAudio thread and install the proper PulseAudio utilities so that you can properly monitor volume levels, and also keep in mind that the ALSA volume controls still apply. You can access the "hardware" mixer via:

```
$ alsamixer -Dhw
```

N.B. The -Dhw switch is necessary as the default ALSA device is now "pulse" in Intrepid. This may cause unintended confusion for users who expect the default device to be their physical hardware.

---

