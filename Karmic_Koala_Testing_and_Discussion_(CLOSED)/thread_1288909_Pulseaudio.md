---
title: "Pulseaudio"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ayates on 2009-10-11
Will wonders ever cease ? After today's pulse updates my volume and clarity of sound are finally on par with Windows.
Yea !!  :):)

---

### Post by coldReactive on 2009-10-11
Well, starting with 9.10, it should have better integration (but this means esound installing may have issues.)

Though, I felt it had pretty good quality even back in 7.04

---

### Post by pt123 on 2009-10-18
one of the developers has slammed Ubuntu on his blog
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)
> 
So in the past Ubuntu packaged PA in a way that, let's say, was not exactly optimal. I thought they'd gotten around fixing things since then. Turns out they didn't. Seems in their upcoming release they again did some genius thing to make PA on Ubuntu perform worse than it could. The Ubuntu kernel contains all kind of closed-source and other crap to no limits, but backporting a tiny patch that is blessed and merged upstream and in Fedora for ages, that they won't do. Gah.


---

### Post by kansasnoob on 2009-10-18
Well, I'm still irritated as hell here!

Pulse audio hasn't been a problem for me since about 8.04.1 but now they seem to be dropping the VIA toggles from alsa-mixer which is a disaster for me!

Actually a disaster X 30 since I'm responsible for thirty plus machines with VIA 82XX sound cards:(

---

### Post by edin9 on 2009-10-18
> **kansasnoob said:**
> Well, I'm still irritated as hell here!

Pulse audio hasn't been a problem for me since about 8.04.1 but now they seem to be dropping the VIA toggles from alsa-mixer which is a disaster for me!

Actually a disaster X 30 since I'm responsible for thirty plus machines with VIA 82XX sound cards:(

 Yeah Pulse sucks. Bad break man.

---

### Post by psyke83 on 2009-10-18
> **kansasnoob said:**
> Well, I'm still irritated as hell here!

Pulse audio hasn't been a problem for me since about 8.04.1 but now they seem to be dropping the VIA toggles from alsa-mixer which is a disaster for me!

Actually a disaster X 30 since I'm responsible for thirty plus machines with VIA 82XX sound cards:(

PulseAudio "isn't a problem" in Hardy because it's not configured properly - ALSA applications completely bypass PulseAudio (because the ALSA -> PulseAudio plugins were immature at the time of release).

Since Jaunty, PulseAudio is configured to intercept ALSA application by default, but this introduces new problems due to certain applications that abuse the ALSA API (e.g., Skype).

What "VIA toggles" are you talking about? PulseAudio is not preventing you from accessing any mixer settings. If you can't find the mixer you want from the "alsamixer" application, then it's the fault of ALSA, not PulseAudio.

---

### Post by Sophont on 2009-10-19
> **kansasnoob said:**
> Well, I'm still irritated as hell here!

Pulse audio hasn't been a problem for me since about 8.04.1 but now they seem to be dropping the VIA toggles from alsa-mixer which is a disaster for me!

Actually a disaster X 30 since I'm responsible for thirty plus machines with VIA 82XX sound cards:(

Is there a particular feature that would force you to upgrade to 9.10? If not then skip it and keep 9.04 until 10.04.

I had to skip Intrepid due to a VPN regression - wasn't a big deal.

If you are responsible for 30+ machines than I guess that's for office/school? Probably not a good idea to upgrade every 6 months anyway.

---

### Post by Joe_Bishop on 2009-10-19
> **pt123 said:**
> one of the developers has slammed Ubuntu on his blog
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)
another confirmation ubuntu sux

---

### Post by Keyper7 on 2009-10-19
> **pt123 said:**
> one of the developers has slammed Ubuntu on his blog
[http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)

More than just one of the developers, I think this guy is the Pulseaudio creator.

---

