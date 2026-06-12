---
title: "[SOLVED] No sound with Audigy2"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Xgen on 2008-10-03
No ALSA problem with Hardy. With Intrepid, ALSA does not work with Mplayer, Exaile, Amarok or system sounds. Music DOES play when pausing the mouse over an mp3 icon. I do have an asoundconf and asoundrc file in my home directory. Tried Pulseaudio with all stages and kernels of Intrepid but have never been able to get sound, using instructions from various Internet sources. So, basically using the exact same ALSA setup as Hardy does not work for me with Intrepid. I welcome any any suggestions. Presently, I am using the Beta and 2.6.27-5.

---

### Post by ktp on 2008-10-03
You shouldn't need to use asoundconf files anymore, since 8.10 is configured to use pulseaudio if the server is running when app uses ALSA defult. 

Could you please try to do the following and see if things work:

1. Kill pulseaudio, either by using "killall pulseaudio" or "pulseaudio -k"
2. Remove all .pulse files from your home directory, "rm -r ~/.pulse*"
3. Move any .asoundrc files away to a temporary directory, of if you have nothing in them that you want to keep, delete them.
4. Restart pulseaudio, either by rebooting, logging out and back in, or running "pulseaudio -D --log-target=syslog"

---

### Post by mc4man on 2008-10-03
With my aud 2's in 8.04 the  'audigy analog/digital output jack' needed to be enabled. In 8.10 it needed to be be disabled.

If you want to check, double left click on the speaker icon in upper panel -> switches.
(if not there use r. click on panel -> add applet

---

### Post by Xgen on 2008-10-03
Thanks for your replies...
    KTP: Did as you suggested and you are right, it doesn't need the alsa files anymore, but the sound didn't reappear. BUT playing around with the individual settings in the programs corrected some problems. This is my present configuration:

Menu-->System-->Preferences-->Sound....all playbacks are Audigy MultiChannel playbacks. Doesn't presently work with PulseAudio or Autodetect.
Volume Control-->Device: Audigy2 (alsa mixer).  Switches: Audigy Analog/DIgital Output ON Tone: ON.
Mplayer: Preferences-->Audio-->ALSA driver-->Configure driver-->Device: surround51.
Exaile: Preferences-->Advanced-->Playback sink: Use GConf Settings.

Haven't found one for Amarok, as yet, but as soon as I replaced the default settings in Mplayer and Exaile the sound appeared. I will try to fine-tune it some more, but I am satisfied that the problem is SOLVED (when I can find the SOLVED button)

---

