---
title: "weird really annoying alert sound, even when volume (supposedly) muted?"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Neon Lights on 2009-02-12
Example: Opening an IM window in Pidgin and backspacing with nothing there.

The alert is startling loud, because it doesn't obey the volume applet, it comes out whatever volume the speaker is turned up to. (mine are always up to full, I just use the volume applet to turn it up and down.)

Is this happening to anyone else? Is there a known reason for it? xD It's really...annoying.

---

### Post by inportb on 2009-02-12
Sounds like the PC [motherboard] speaker to me. You should try disabling it.

---

### Post by Mazza558 on 2009-02-12
Follow this guide to disable it:

[http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/]("http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/")

---

### Post by Neon Lights on 2009-02-12
> **inportb said:**
> Sounds like the PC [motherboard] speaker to me. You should try disabling it.
It's coming out my regular speakers though...same sound I think though. >.<

---

### Post by Mazza558 on 2009-02-12
> **Neon Lights said:**
> It's coming out my regular speakers though...same sound I think though. >.<

Have you tried the guide I posted yet?

---

### Post by Neon Lights on 2009-02-12
> **Mazza558 said:**
> Have you tried the guide I posted yet?
I did anyway, yeah. Didn't work.

---

### Post by khc on 2009-02-12
If other applications can play sound, then you've not muted the speakers.

---

### Post by Neon Lights on 2009-02-12
> **khc said:**
> If other applications can play sound, then you've not muted the speakers.
They can't. Nothing makes a sound except for the same alert, and only when using Tab complete in the terminal, backspacing with nothing in the terminal and pidgin, etc.

---

### Post by yelo3 on 2009-02-13
To mute the alerto sound run:
alsamixer -Dhw
with arrow keys move to PC Beep
hit 'm' and 'Esc'

---

### Post by Neon Lights on 2009-02-13
> **yelo3 said:**
> To mute the alerto sound run:
alsamixer -Dhw
with arrow keys move to PC Beep
hit 'm' and 'Esc'
That gives out
```
alsamixer: function snd_ctl_open failed for hw: No such file or directory
```

---

### Post by Neon Lights on 2009-02-19
Tried alsamixer again after updates and stuffs.

Muting "IEC958D" solved it.

---

### Post by Neon Lights on 2009-02-24
Okay, rebooted, and it reset. Any idea how to make that a permanent change? It's REALLY irritating.

---

