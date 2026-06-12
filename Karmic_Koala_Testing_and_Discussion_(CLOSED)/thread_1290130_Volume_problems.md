---
title: "Volume problems"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whitethorn on 2009-10-13
Hi,

I kind of have a problem with the new sound plugin.  Whenever I restart my pc the pcm volume is full which causes some really nasty kinda high pitched noise, when I use alsamixer to put it down a 3 db it sound normal. If I use the volume plugin on the desktop it also turns up the volume on the master channel as well as the pcm which then makes it sound like crap again.  So after every reboot I need to fire alsamixer up set the volume levels and then use the volume control on my speakers.  I hope this gets fixed or at least someway of controlling which channels get used.

---

### Post by seamuso on 2009-10-13
try this - Set your alsamixer how you need it to be .. after you hit esc,

```
sudo alsactl store
```

That should hold the settings for you

---

### Post by whitethorn on 2009-10-14
> **seamuso said:**
> try this - Set your alsamixer how you need it to be .. after you hit esc,

```
sudo alsactl store
```

That should hold the settings for you

I tried that it didn't work.  Gah a tad bit annoying.

---

### Post by Sandsound on 2009-10-15
> **whitethorn said:**
> I tried that it didn't work.  Gah a tad bit annoying.

after you run :
```
sudo alsactl store
```

then add the folowing in system/preferences/startup applications :
```
alsactl restore
```

like this :
[IMG]http://www.sandgreen.dk/img/pulse_startup.png[/IMG]

---

