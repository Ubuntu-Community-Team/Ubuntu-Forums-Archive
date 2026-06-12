---
title: "BSOD on ibex"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by insane_alien on 2008-08-15
So, in the past hour of testing the ibex i have encoutered some interesting deaths of it.

first one up, BSOD, beige screen of death
second, GSOD, green screen of death
third, WSOD, white screen of death
fouth, SSOD, scrambled screen of death

all of these are identical except for what happens to the screen.

i go to play a music or video file and that happens. can't even drop to the command line. the audio still plays though.

as far as i can tell it is media player and media type independant and random as well.

i'm running ubuntu 64-bit on a Dell inspiron 1525 laptop with 4GB of RAM

---

### Post by Nullack on 2008-08-16
synch to repos and try again xorg was update recently. Use an uptodate mirror so your not behind :)

---

### Post by insane_alien on 2008-08-16
okay got the new xorg, hasn't happened yet but could still be lurking

---

### Post by BlueSkyNIS on 2008-08-16
I didn't know Ibex had an BSOD.. Can you post a pic when/if it happens, I'm curious? :)

---

### Post by insane_alien on 2008-08-16
i can't do anything when it happens.

it is easy to describe though. for the beige screen of death, the screen goes completely beige, sometimes flickering to black.

for the green screen of death replace beige with green, same for white.

the scrambled screen of death is basically the screen i was just looking at but heavily scrambled.

---

### Post by BlueSkyNIS on 2008-08-16
If I understand you correctly you are describing just plain erroneous screen, and not the official BSOD screen that developers were talking about...

---

### Post by Nullack on 2008-08-16
Linux kernels go into a panic, not a BSOD

---

### Post by insane_alien on 2008-08-16
i know that. its not a kernel panic. its just a complete and utter failure of all devices that interface with the outside world except the speakers. i tried running a shutdown command blind but it didn't work.

it is effectively a screen of death as it requires a reboot to fix.

just got another whitescreen watching a video. new xorg didn't fix it.

---

### Post by go7Ul1ai on 2008-08-16
> **insane_alien said:**
> i know that. its not a kernel panic. its just a complete and utter failure of all devices that interface with the outside world except the speakers. i tried running a shutdown command blind but it didn't work.

it is effectively a screen of death as it requires a reboot to fix.

just got another whitescreen watching a video. new xorg didn't fix it.

I've had this recently, except I'm using Hardy Heron -_-

---

### Post by solitaire on 2008-08-16
Is it just me ? But every time i hear about a 'kernal panic' i imagine the cpu jumping out of the case, arms waving wildly, screaming it's head off while it runs around the room!!!!

Oh!
Probably just me then..... :)

---

### Post by Steveway on 2008-08-16
> **solitaire said:**
> Is it just me ? But every time i hear about a 'kernal panic' i imagine the cpu jumping out of the case, arms waving wildly, screaming it's head off while it runs around the room!!!!

Oh!
Probably just me then..... :)

Theoretically spoken this is pretty much what happens at a kernel-panic.

---

