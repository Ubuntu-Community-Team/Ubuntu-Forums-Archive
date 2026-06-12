---
title: "Downgrading from 8.10 to 8.04, big Intrepid issues"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rezfiles on 2008-10-19
Hey Everyone.
Yesterday I upgraded my install from 8.04 to 8.10 and now I'm having major issues.
1. My ALSA drivers are really messed up, I only get sound from my soundblaster Audigy ZS 2 using PulseAudio drivers. Firefox won't play sounds as well.. How do I reinstall ALSA drivers fully? How would I go about fixing this?

2. X server does not start on startup. I have to login and type startx to get into the GUI. I have all of the latest NVIDIA 177 drivers. How do I fix this?

3. None of my extra drives will mounts. I have two internal ntfs SATA drives. I try to mount them manually, nothing happens.

Can I just go back to 6.04 where everything worked fine, Or is there some way to fix this chaos?

Thanks!

---

### Post by mikewhatever on 2008-10-19
There isn't a way to downgrade, afaik. It looks like your options are reinstall or troubleshoot.

---

### Post by ktp on 2008-10-19
in 8.10 pulseaudio auto detects and uses ALSA plugin.  so if you have any .asound* configs try removing them.  also try cleaning ~/.pulse/*.

---

### Post by gtdaqua on 2008-10-20
If you have the root and home partitions separated then you can seamlessly move to hardy. Just install hardy 8.04.1 over the current installation and specify the installer to format "/" only. After a few mins you shud be back in hardy - I have done this several times when alpha/beta releases simply fail or lock out. You can specify the same username and the same home partition - no data loss will occur.

---

### Post by Sef on 2008-10-20
>  Can I just go back to 6.04 where everything worked fine, Or is there some way to fix this chaos?

Do you mean 8.04?  

Back up your data before reinstalling.

> 2. X server does not start on startup. I have to login and type startx to get into the GUI. I have all of the latest NVIDIA 177 drivers. How do I fix this?

What are your system specs?

---

### Post by amoresunaramera on 2008-10-21
> **gtdaqua said:**
> If you have the root and home partitions separated then you can seamlessly move to hardy. Just install hardy 8.04.1 over the current installation and specify the installer to format "/" only. After a few mins you shud be back in hardy - I have done this several times when alpha/beta releases simply fail or lock out. You can specify the same username and the same home partition - no data loss will occur.


this sounds interesting... if i don't have them (the home root and home partitions) separated, is there a way for me to separate them so that i may do this?

---

### Post by MALEADt on 2008-10-21
> **amoresunaramera said:**
> this sounds interesting... if i don't have them (the home root and home partitions) separated, is there a way for me to separate them so that i may do this?

Off course there is, open up google, enter some search queries and pick one of the billion tutorials which have been written on that subject.

---

### Post by Archmage on 2008-10-21
Kindly note that 8.10 are still in Beta-stage. You shouldn't use it on your productive system.

---

