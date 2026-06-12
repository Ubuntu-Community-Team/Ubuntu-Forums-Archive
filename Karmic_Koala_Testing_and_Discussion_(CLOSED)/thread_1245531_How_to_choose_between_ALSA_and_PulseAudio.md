---
title: "How to choose between ALSA and PulseAudio?"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ric_NYC on 2009-08-20
I didn't find where to change the audio in Karmic Koala.

Any help is appreciated!


Thanks.

---

### Post by scaine on 2009-08-20
I'm not sure you can.  It would help your thread to be answered if you described WHY you want to "choose between ALSA and PA".  PA is the Karmic standard.  In fact, it's been standard, I believe, since Hardy (8.04).  This alpha version, Karmic, I believe makes it quite difficult to turn off PA, although this was possible in Intrepid by pkill'ing the pulseaudio process, or simply un-installed the pulse packages - I don't think it's that straight forward any more.

Maybe you just need to install padevchooser or something? [sudo apt-get install padevchooser]

Best help to get PA working on your system.  Doing so will likely help others and in future releases of Ubuntu and other distros which use PA, things will be more and more stable, reliable and feature filled.

Or, have a good rant about why PA doesn't work for you.  It's been done a thousand times before (there's another search, right there), knock yourself out.  Everyone on the forums lives for that stuff. /sarcasm

The choice is yours.

---

### Post by Ric_NYC on 2009-08-20
I was playing Quake Live and my computer had no sound.
I tried to switch to ALSA. Then I didn't find a way to do that.

Switching to ALSA solved some issues I had before. That's why I tried it.

---

### Post by shakaran on 2009-08-20
You can try gnome-alsamixer for do some tricks more than pulseaudio.

---

### Post by Ric_NYC on 2009-08-20
> **shakaran said:**
> You can try gnome-alsamixer for do some tricks more than pulseaudio.


Thanks. I'll try it.

---

### Post by BwackNinja on 2009-08-20
I don't think gnome-alsamixer will do much good now that pulseaudio has taken over the volume control sliders. Its still nice if you're only using alsa though.

---

### Post by shakaran on 2009-08-20
I use it for control PCM or others. With pulseaudio I dont know how to change PCM.

---

### Post by crimsun on 2009-08-21
To disable PA, there are four steps:

1) echo autospawn = no|tee -a ~/.pulse/client.conf
2) touch ~/.pulse_a11y_nostart
3) sudo chmod 600 /usr/bin/pulse-session
4) killall pulseaudio

---

### Post by psyke83 on 2009-08-21
> **crimsun said:**
> To disable PA, there are four steps:

1) echo autospawn = no|tee -a ~/.pulse/client.conf
2) touch ~/.pulse_a11y_nostart
3) sudo chmod 600 /usr/bin/pulse-session
4) killall pulseaudio

Maybe it would be a good idea if we could simplify this process for users? Having the ability to disable PulseAudio would be useful for troubleshooting (and distinguishing between PulseAudio and) ALSA issues.

---

### Post by gradinaruvasile on 2009-08-21
U can remove/disabled pulseaudio and use alsamixer (the terminal version). Tried and works.

---

