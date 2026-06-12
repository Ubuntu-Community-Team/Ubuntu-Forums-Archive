---
title: "CPU and I/O problems with banshee 1.5"
date: 2009-06-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-06-09
I've been having major issues with banshee 1.5. It takes up 100% of CPU on one of my cores, and using iotop I can see that it's *constantly* making reads of the order of 1000 KB/s.

I had problems with the previous version of banshee in jaunty - I would occasionally experience very high CPU loads with the only way to stop the high usage being to kill banshee-1.

This seems to be a major regression to me; is anyone else experiencing this?

---

### Post by jmmL on 2009-06-09
Haha
After a few days of thinking about what it might be about; I finally had a thought: the BPM calculator!

Disabling that in the preferences brings disk and CPU activity back to normal. I'd let banshee run for about an hour before to see if it was doing something like this; but it didn't stop. I guess I didn't give it long enough to go through my library.

Feel like a bit of a muppet now... :p

---

### Post by Incognito-Here on 2009-06-10
Half-ready. Must not be the default at least.

---

### Post by zekopeko on 2009-06-10
> **Incognito-Here said:**
> Half-ready. Must not be the default at least.

You are right! a math intensive operation shouldn't use your CPU like that! /sarcasm.

---

### Post by Incognito-Here on 2009-06-10
Three of four years ago I played with foobar 2000 on my windows. It also has bpm calculator, but it doesn't eat 100% cpu ;) It takes at most 5% of my Athlon XP 2500 ;)
So, it's mono ;)

---

### Post by Swarms on 2009-06-10
> **Incognito-Here said:**
> Three of four years ago I played with foobar 2000 on my windows. It also has bpm calculator, but it doesn't eat 100% cpu ;) It takes at most 5% of my Athlon XP 2500 ;)
So, it's mono ;)

Or is it satan? Oh I forgot that is the same to you.

---

### Post by zekopeko on 2009-06-10
> **Incognito-Here said:**
> Three of four years ago I played with foobar 2000 on my windows. It also has bpm calculator, but it doesn't eat 100% cpu ;) It takes at most 5% of my Athlon XP 2500 ;)
So, it's mono ;)

and you are basing your conclusion on what evidence?

---

### Post by directhex on 2009-06-10
> **jmmL said:**
> Haha
After a few days of thinking about what it might be about; I finally had a thought: the BPM calculator!

Disabling that in the preferences brings disk and CPU activity back to normal. I'd let banshee run for about an hour before to see if it was doing something like this; but it didn't stop. I guess I didn't give it long enough to go through my library.

Feel like a bit of a muppet now... :p

Accurate pre-emptive BPM detection (i.e. as opposed to guessing based on the current second of playback, as done by most Windows apps) is a very intensive operation (I did my degree third-year project on it, so trust me). So, sadly, it's something which simply needs to eat up your CPU. The unofficial Mirage extension is similar. I believe it shouldn't impact on your playback, as inside the app, "low priority" tasks yield to "High priority" tasks like playback. It might affect the rest of your system's responsiveness though, so the pressing question should be asked - was this on by default? Doesn't seem to be to me.

---

### Post by jmmL on 2009-06-10
> **directhex said:**
> Accurate pre-emptive BPM detection (i.e. as opposed to guessing based on the current second of playback, as done by most Windows apps) is a very intensive operation (I did my degree third-year project on it, so trust me). So, sadly, it's something which simply needs to eat up your CPU. The unofficial Mirage extension is similar. I believe it shouldn't impact on your playback, as inside the app, "low priority" tasks yield to "High priority" tasks like playback. It might affect the rest of your system's responsiveness though, so the pressing question should be asked - was this on by default? Doesn't seem to be to me.

This isn't on by default. One bit of weirdness is that there are two seemingly identical checkboxes to enable bpm detection, I've ticked one or the other or both and it doesn't seem to make a difference to resources used.

It would be nice to have control over how much of the CPU it gets to use though. Mirage is also pretty resource-hungry, but it finishes much quicker than the bpm detection. There were a few times that my playback skipped momentarily, so the priority system wasn't quite working perfectly. It was the disk-reads more than anything that annoyed me.

Still, these are all still wish-list items (although I think they should be fairly high up). Contrary to my initial post, this is most definitely ***not*** a regression.

---

