---
title: "sound not workin after update"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by giorsat on 2009-03-10
after today update, I've no sound at all in banshee and rhythmbox nor totem. while vlc makes only noise.
Idem if I try the sound optiond
I have a pavilion dv7 with ICH9 intel sound
until yesterday everything was ok

---

### Post by nyarnon on 2009-03-10
Hmmm rhythmbox indeed stalls but totem runs fine here, anyway the sound system is under full development read the sticky and add the ppa.

**Correction:** after switching to the pulse mixer everything runs fine. Alsa problem?

---

### Post by giorsat on 2009-03-10
can you please tell me how to fix the problem?
should I add ppa to the sources and download the new pulseaudio testing?

---

### Post by giorsat on 2009-03-10
alsa is not workin at all. I disabled pulse to use only alsa but it still gives me problems with stuttering sounds . It is like the sound gets rallented and loops indefinetely.

---

### Post by nyarnon on 2009-03-10
Yes please guys, read the sticky and add the crimson ppa it will solve your problem, as of today pulse seems to work just fine as you can read in that thread.

@giorsat

Yes add de aptline to the list of repositories. As you have to ask the easiest methode will be doing it through synaptic. Then add the pgp key for the ppa and update.

If any of you disabled the pulse entries in startup programs (formerly gnome-sessions) do not forget to enable them again.

---

### Post by giorsat on 2009-03-10
WORKING! I added the repo and updated pulseaudio- reboot-. now it works like a charm! thank you!

---

### Post by giorsat on 2009-03-12
sorry to say but today, after update, sound is completely missing
why ich9 soundcard is so problematic.
the same update on other computers gave no problem
any idea?

---

