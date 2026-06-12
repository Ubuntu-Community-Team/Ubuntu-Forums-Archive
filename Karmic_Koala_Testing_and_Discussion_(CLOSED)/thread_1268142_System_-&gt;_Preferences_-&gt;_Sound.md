---
title: "System -&gt; Preferences -&gt; Sound ???"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Xamiga on 2009-09-16
I've lost my System -> Preferences -> Sound.
What is the executable that it uses?

---

### Post by MJWitter on 2009-09-16
gnome-volume-control

---

### Post by VMC on 2009-09-16
> **Xamiga said:**
> I've lost my System -> Preferences -> Sound.
What is the executable that it uses?

```
/usr/bin/gnome-volume-control

```

---

### Post by Podex on 2009-09-16
I remember I had two instances of Sound in the Preferences menu before and now I have one. Maybe whatever they did to fix that made you lose the only one you had.

---

### Post by Xamiga on 2009-09-16
VMC: Thanks.   
  Another problem: gnome-volume-control just hangs with 'Waiting for sound system to respond'

Perhaps because I removed pulseaudio....

Podex: Thanks,  I remember having 2 at one point.

---

### Post by chrisccoulson on 2009-09-16
Yes, it won't work without Pulseaudio

---

### Post by DevilInPgh on 2009-09-20
I have Pulseaudio installed, yet am still having the same issue trying to run gnome-volume-control.  For the meantime, I am using alsamixer in the terminal.

---

