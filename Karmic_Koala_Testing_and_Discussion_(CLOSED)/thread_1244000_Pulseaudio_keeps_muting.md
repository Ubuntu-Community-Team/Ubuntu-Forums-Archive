---
title: "Pulseaudio keeps muting"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-19
Is it normal for Pulseaudio to persistently mute itself after an audio stream ends?

---

### Post by Starks on 2009-08-19
Anyone else experiencing this?

Alsa Mixer doesn't help.

---

### Post by qamelian on 2009-08-19
> **Starks said:**
> Anyone else experiencing this?

Alsa Mixer doesn't help.
I was experiencing this on my test box after a nasty lockup while installing updates. After fiddling with it for a while, though I just said the heck with it and did a fresh install of alpha 4 and haven't seen the issue since. Previously, I had been on an install that had started with an install of alpha 3 and updated from there.

---

### Post by trulan on 2009-08-19
It mutes after lots of things, not just an audio stream.  Open and close any window and it mutes.  Very annoying.

---

### Post by Luca_turicci on 2009-08-20
Hi, i'm having the same problem, plus, yesterday tuxguitar was working flawless, but after the updates i did last night, it stopped working... 

BTW, anyone has tried Ubuntu Studio 9.10?

---

### Post by rudenko_ruslan on 2009-08-20
> **Starks said:**
> Anyone else experiencing this?
Yup, encountered with this issue today. Also, sound is muted at startup (I've updated to a [new test PA package]("https://lists.ubuntu.com/archives/karmic-changes/2009-August/006715.html")).

---

### Post by morryis on 2009-08-20
Perhaps it is bug [403859]("https://bugs.launchpad.net/bugs/403859"), please confirm!

---

### Post by Luca_turicci on 2009-08-20
I don't think it's the same bug, at least for me, since when I run totem it's perfect, in fact, i just noticed that youtube videos make no sound either, but totem is perfect.

---

### Post by crimsun on 2009-08-20
This symptom should be resolved as of the latest upload (1:0.9.16~test5-0ubuntu1) to Karmic.

---

### Post by trulan on 2009-08-20
> **Luca_turicci said:**
> Hi, i'm having the same problem, plus, yesterday tuxguitar was working flawless, but after the updates i did last night, it stopped working... 

BTW, anyone has tried Ubuntu Studio 9.10?
I can confirm that the latest update fixes this problem.

I am using Ubuntu Studio 9.10.  And I see they have yet another RT kernel upgrade on the way!  I have yet to try tuxguitar on Karmic.

I started a thread over in the MM production section to try to generate some interest, as no one here seemed to be talking about Studio or the RT kernel.
[http://ubuntuforums.org/showthread.php?t=1241103](http://ubuntuforums.org/showthread.php?t=1241103)

---

### Post by morryis on 2009-08-20
> **crimsun said:**
> This symptom should be resolved as of the latest upload (1:0.9.16~test5-0ubuntu1) to Karmic.

Looks like it is solved for totem with latest pulseaudio update for me, volume level does not change on skip any more. 

With audacious2 (Pulseaudio output plugin) I still experience volume decrease. In gnome-volume-control, 'Output volume' does not change while per application volume level still decreases on next track.

---

### Post by Starks on 2009-08-20
test5 seems to have fixed the issue for the most part.

---

### Post by zoomy942 on 2009-08-21
where can i get this update?

---

### Post by taavikko on 2009-08-21
> **zoomy942 said:**
> where can i get this update?

Using main server on updates, local mirrors may be out of sync seeveral days.

---

### Post by Luca_turicci on 2009-08-22
I've been checking for updates twice a day, and now the problem is partially gone, doesn't mute every now and then, but seems like it mutes on startup, but i like that, i don't really like the Ubuntu startup sound =)

---

