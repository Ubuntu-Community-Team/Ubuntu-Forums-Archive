---
title: "Unable to burn a cd in Brasero..."
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-01-18
Ater preparing all the files in Brasero, I choose "Write to disk", Brasero closes and...
If I try to copy CD, same thing happens...
Any ideas?
(Tried with gksudo, tried all different scenarios, everything goes OK, until something is to be wrote on to disk...)

---

### Post by Hogosha on 2010-01-18
I had some problems with it so i switched to a program called GnomeBaker. it works great.

---

### Post by netbuk on 2010-01-18
what about nero?

---

### Post by lidex on 2010-01-18
Run brasero from a terminal and post the output of same here so we can see what the error is. In a terminal:
```
brasero
```
Then replicate the conditions that caused the error.

Have you made any recent changes to your system, updates, etc? Was it working before? Also check your logs. Try /var/log/messages.

---

### Post by MacUntu on 2010-01-18
> **netbuk said:**
> what about nero?

Using Nero won't fix Brasero.

---

### Post by zika on 2010-01-18
> **lidex said:**
> Run brasero from a terminal and post the output of same here so we can see what the error is. In a terminal:
```
brasero
```Then replicate the conditions that caused the error.

Have you made any recent changes to your system, updates, etc? Was it working before? Also check your logs. Try /var/log/messages.I'm on Lucid, up-to-hour. I did not need to burn CD lately so I do not know the exact moment when this started. I'll make a "report"...
Update: I'll be damned, It burned now a folder I wanted to save. The only difference is that I called it from Terminal and that I was in KMS... (Previously I trid in the same kernel .6.33-999 but without KMS...) I'll investigate more...

---

### Post by phillw on 2010-01-18
The joys of testing ... one day it doesn't work ... then .. woosh, it does ;-)

Not too sure when the last update of Basero or dependent files was done, none show at [https://launchpad.net/ubuntu/lucid/+queue?queue_state=2&queue_text=Brasero](https://launchpad.net/ubuntu/lucid/+queue?queue_state=2&queue_text=Brasero)

Phill.

---

### Post by VMC on 2010-01-18
> **MacUntu said:**
> Using Nero won't fix Brasero.

LOL, Duh.

I only have problems with Brasero if I remove the already mounted cd with another one without using the eject instead of pushing the eject button.

---

### Post by phillw on 2010-01-18
> **netbuk said:**
> what about nero?

Wow ?!!! How did I miss that ? Nero for Ubuntu ? OMG !!!

Bless ;)

Phill.

---

### Post by lmedinas on 2010-01-18
Try brasero -g and see if there's any bug open. Most of the time is problems related with cdrkit not brasero, you can try other backends.

---

