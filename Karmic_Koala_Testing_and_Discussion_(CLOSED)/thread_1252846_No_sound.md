---
title: "No sound"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sockerdrickan on 2009-08-29
Hi I have an M-Audio Revolution 7.1 pci sound card. It is recognized by Ubuntu and I can set some volume controls. The thing is I do not get any sound output whatsoever.

Alsa is 1.0.20 as per Ubuntu 9.10

---

### Post by taavikko on 2009-08-29
Does alsa work?
```
aplay /usr/share/sounds/question.wav
```

Check the channels, muted?
```
alsamixer
```

Does pulse use the correct output
```
gnome-volume-control
```

---

### Post by askBob on 2009-08-29
> **taavikko said:**
> Does alsa work?
```
aplay /usr/share/sounds/question.wav
```

Check the channels, muted?
```
alsamixer
```

Does pulse use the correct output
```
gnome-volume-control
```
Yes ...all the above should help.  I finally got my sound working after
1.  installing all ALSA packages
2.  unmuting the volume in the Gnome volume control (top right side of screen)
3.  turning up volume for PCM ...the only way I found this was to launch the Gnome volume control manually, by typing 'gnome-volume-control' in a terminal window.
 
Good luck!

---

### Post by Sockerdrickan on 2009-08-29
Still does not work :( And I have no idea why, I feel so helpless when it comes to sound related troubles...

---

### Post by taavikko on 2009-08-29
> **Tux0r said:**
> Still does not work :( And I have no idea why, I feel so helpless when it comes to sound related troubles...

If system is an upgrade from 9.04, delete (while no running gdm) .pulse* and .asoundrc
and start gdm again.

Does, "gnome-volume-manager" show anything related to output devices?

One can also test with
```
gstreamer-properties
```
that audio test produces a sound with alsa/pulse, set it to autodetect.

---

### Post by Sockerdrickan on 2009-08-29
> **taavikko said:**
> If system is an upgrade from 9.04, delete (while no running gdm) .pulse* and .asoundrc
and start gdm again.
Thanks now it works!! :popcorn:

FYI I did a clean 9.10 install

---

### Post by taavikko on 2009-08-29
> **Tux0r said:**
> Thanks now it works!!
You're welcome

[quote=Tux0r]FYI I did a clean 9.10 install[/QUOTE]
So, somehow ~/.pulse* got corrupted somehow...

---

