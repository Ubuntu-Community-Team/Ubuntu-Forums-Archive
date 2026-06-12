---
title: "Upgraded to Feisty, lost audio"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by kilgore731 on 2007-04-20
I'm using a M-audio delta 1010lt sound card.  In edgy I had sound playback working but I was getting odd noise from one channel.  I upgraded to feisty today and lost the audio entirely.  

In the device manager the card shows up as ICE1712[Envy] PCI Mulit-Channel I/O Controller, with multiple ALSA and OSS entries below it including one M1010LT ALSA Control Device.  Under Sound Preferences, when I select the ICE1712 multi (which worked under Edgy) or ALSA and click Test, I get an error.  

audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink: 
Could not open resource for writing.

Any ideas?  I've been Googleing all day with no luck.  Any and all pointers as to how to correctly configure this card are greatly appreciated.

---

### Post by kilgore731 on 2007-04-20
after reseting the soundcard with 

asoundconf reset-default-card

I am able to get the test tone in both sound settings and Multimedia Systems Selector, but I still can't get the sound to work in any applications.  I can get the test tone with both the analogue and s/pdif outputs. Any suggestions would be great.

---

### Post by WireMX on 2007-04-20
I having the same problem I get this:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el recurso para escritura.

I used t have sound with Ubuntu 7.04 Beta, but now I'm mute!

I'm new in Ubuntu.... please help us,

Thanks!

---

### Post by fschaefer on 2007-04-21
I had the same Problem; funny enough, a simple

```
asoundconf reset-default-card
```

did it ;)

---

### Post by WireMX on 2007-04-22
> **fschaefer said:**
> I had the same Problem; funny enough, a simple

```
asoundconf reset-default-card
```

did it ;)

It didnt work for me, still no sound... what could be the problem?

---

### Post by monchichi on 2007-04-25
I have the same card, had the same problem. For me, it turned out that a couple of programs were calling esd or otherwise using the device. So, turning off sound in Gaim, and turning off ESD in Sound Preferences fixed the problem for me.

---

