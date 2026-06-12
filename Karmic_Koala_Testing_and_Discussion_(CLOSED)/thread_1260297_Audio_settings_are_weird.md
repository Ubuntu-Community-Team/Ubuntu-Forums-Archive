---
title: "Audio settings are weird"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vfontanela on 2009-09-07
I don't know what happens with audio settings here. I'm using Alpha 5. And my laptop's integrated sound card is a Realtek ALC883 (at least the system identified it as this)

* When I boot, my sound is set automatically mute. And if I don't click several times in the volume control to increase the volume, it doesnt work.

* I used plug some big speakers at my laptops output jack, and then the audio was played at the big speakers, but now the sound is divided in channels and I have part of the audio in the front speakers and the other part in the big speakers. Like, if it is a song: vocal at the front, musical instruments at the big speakers, which is bad to me. Following instructions I found at the web, I installed Gnome Alsa Mixer, and since then even with the regular volume control at 100%, I have to set the front speakers at G Alsa Mixer, because it sets mute automatically.

It is really strange, because my audio card was always fully supported since I started using Ubuntu (Hardy Heron).

Any help is appreciated.

PS: Besides this issue, my Ubuntu A5 KK works perfectly.

---

### Post by zoomy942 on 2009-09-07
welcome to Pulse audio

---

### Post by vfontanela on 2009-09-07
But I was using PulseAudio in Jaunty and it was ok.

---

### Post by patasenko on 2009-09-07
Well at least PulseAudio actually recognizes your sound card, I am still finding it difficult to make PA detect my sound car alc660-vd... as i have nothing in the settings of sound, not even HDMI, which accidently was on there during 1 boot, out of 10. Well at least welcome to the development side.

---

### Post by vfontanela on 2009-09-07
Is there a way to solve it? Like changing Pulse for Alsa or Oss?

---

### Post by zoomy942 on 2009-09-07
i havent forgotten. :)  its on my work PC.  im running up to work in a ew horus.  i will post it

---

### Post by hanzomon4 on 2009-09-08
Sounds like a problem with ALSA.... do you have an old asound.conf anywhere?

---

### Post by vfontanela on 2009-09-08
No, I don't have, because I formated the partition I had Jaunty to install KK.

What if I run Jaunty Live CD, look for asound.conf of the live cd? Is that one ok?

---

### Post by jocko on 2009-09-08
> **vfontanela said:**
> No, I don't have, because I formated the partition I had Jaunty to install KK.

What if I run Jaunty Live CD, look for asound.conf of the live cd? Is that one ok?
You shouldn't have any asound.conf. It would just interfere with pulseaudio.

---

### Post by tretle on 2009-09-08
oh look more people complaining about pulse audio, shoot me now.

---

### Post by vfontanela on 2009-09-09
The same here after today's updates, which upgraded pulseaudio package.

---

### Post by vfontanela on 2009-09-09
**I have a partial sollution.**

I noticed that after september 9th updates, my pulseaudio was NOT mute anymore at startup. I mean, the volume control was 100%, but no audio till I open Gnome Alsa Mixer and unmute my front speaker.

So i created a script:

[I]amixer set Front 100% unmute
exit
[/I]
and saved as audio.sh at my home, then chmod +x audio.sh

Then I went System, Preferences, Sessions and put my audio.sh at startup, and Voilà.

But I still have a problem. When I plug other speakers it doesnt shut my front speakers up. And sometimes they divide channels. Vocal in the front speaker, instruments at the big speakers. I tried changing alsamixer configs but it didnt work.

Even so, I'm feeling we've made progresses - and noone was shot :P

---

